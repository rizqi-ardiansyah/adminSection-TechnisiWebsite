<template>
  <aside class="main-sidebar sidebar-dark-primary elevation-4">
    <!-- Brand Logo -->
    <inertia-link :href="route('admin.dashboard.index')" class="brand-link">
      <img
        :src="'../images/TechNisiLogo.png'"
        alt="TechNisi Logo"
        class="brand-image img-circle elevation-3"
        style="opacity: 0.8"
      />
      <span class="brand-text font-weight-light">TechNisi</span>
    </inertia-link>

    <!-- Sidebar -->
    <div class="sidebar">
      <!-- Sidebar user panel (optional) -->
      <div class="user-panel mt-3 pb-3 mb-3 d-flex">
        <div class="image">
          <img
            :src="'../images/man.png'"
            class="img-circle elevation-2"
            alt="User Image"
          />
        </div>
        <div class="info">
          <a href="#" class="d-block">{{ $page.props.user.name }}</a>
        </div>
      </div>

      <!-- Sidebar Menu -->
      <nav class="mt-2">
        <ul
          class="nav nav-pills nav-sidebar flex-column"
          data-widget="treeview"
          role="menu"
          data-accordion="false"
        >
          <!-- Add icons to the links using the .nav-icon class
                    with font-awesome or any other icon font library -->
          <li class="nav-item menu-open">
            <inertia-link
              :href="route('admin.dashboard.index')"
              class="nav-link"
              :class="route().current('admin.dashboard.*') ? 'active' : ' '"
            >
              <i class="nav-icon fas fa-tachometer-alt"></i>
              <p>Dashboard</p>
            </inertia-link>
          </li>
          <li class="nav-item">
            <a href="#" class="nav-link">
              <i class="nav-icon fas fa-table"></i>
              <p>
                Tables
                <i class="fas fa-angle-left right"></i>
              </p>
            </a>
            <ul class="nav nav-treeview">
              <!-- <li class="nav-item" v-if="$page.props.auth.hasRole.admin">
                <inertia-link
                  :href="route('admin.admins.index')"
                  class="nav-link"
                  :class="route().current('admin.admins.*') ? 'active' : ' '"
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Admin</p>
                </inertia-link>
              </li> -->
              <li
                class="nav-item"
                v-if="
                  $page.props.auth.hasRole.admin || $page.props.auth.hasRole.user"
                 >
                <inertia-link
                  :href="route('admin.users.index')"
                  class="nav-link"
                  :class="route().current('admin.users.*') ? 'active' : ' '"
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Admin</p>
                </inertia-link>
              </li>
              <li
                class="nav-item"
                v-if="
                  $page.props.auth.hasRole.admin || $page.props.auth.hasRole.user"
                 >
                <inertia-link
                  :href="route('admin.customers.index')"
                  class="nav-link"
                  :class="route().current('admin.customers.*') ? 'active' : ' '"
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Customer</p>
                </inertia-link>
              </li>
              <li
                class="nav-item"
                v-if="
                  $page.props.auth.hasRole.admin || $page.props.auth.hasRole.user"
                 >
                <inertia-link
                  :href="route('admin.technician.index')"
                  class="nav-link"
                  :class="route().current('admin.technician.*') ? 'active' : ' '"
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Technician</p>
                </inertia-link>
              </li>
              <li
                class="nav-item"
                v-if="
                  $page.props.auth.hasRole.admin || $page.props.auth.hasRole.user"
                 >
                <inertia-link
                  :href="route('admin.transaction.index')"
                  class="nav-link"
                  :class="route().current('admin.transaction.*') ? 'active' : ' '"
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Transaction</p>
                </inertia-link>
              </li>
              <li class="nav-item" v-if="$page.props.auth.hasRole.super_admin || $page.props.auth.hasRole.admin">
                <inertia-link
                  :href="route('admin.roles.index')"
                  class="nav-link"
                  :class="route().current('admin.roles.*') ? 'active' : ' '"
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Roles</p>
                </inertia-link>
              </li>
              <li class="nav-item" v-if="$page.props.auth.hasRole.super_admin || $page.props.auth.hasRole.admin">
                <inertia-link
                  :href="route('admin.permissions.index')"
                  class="nav-link"
                  :class="
                    route().current('admin.permissions.*') ? 'active' : ' '
                  "
                >
                  <i class="far fa-circle nav-icon"></i>
                  <p>Permissions</p>
                </inertia-link>
              </li>
            </ul>
          </li>
          <li class="nav-header">MISCELLANEOUS</li>
          <li class="nav-item">
            <inertia-link :href="route('dashboard')" class="nav-link">
              <i class="nav-icon fas fa-home"></i>
              <p>Site</p>
            </inertia-link>
          </li>
          <!-- <li class="nav-item">
            <form @submit.prevent="logout">
             <a href="#" class="nav-link">
              <i class="nav-icon fas fa-sign-out-alt"></i>
              <p>Logout</p>
            </a>
            </form>
          </li> -->
          <li class="nav-item">
            <form @submit.prevent="logout">
              <button type="submit" class="nav-button">
                <i class="nav-icon fas fa-sign-out-alt"></i>
                <p>Logout</p>
              </button>
            </form>
          </li>
        </ul>
      </nav>
      <!-- /.sidebar-menu -->
    </div>
    <!-- /.sidebar -->
  </aside>
</template>
<script>
export default {
  methods: {
    logout() {
      this.$inertia.post(route("logout"));
    },
  },
};
</script>
