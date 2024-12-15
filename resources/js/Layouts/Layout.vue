<script setup>
    import { Link } from '@inertiajs/vue3';
</script>
<template>
    <div>
        <header>
            <nav >
                <div class="space-x-6">
                    <Link :href="route('home')" class="nav-link"
                     :class="{'bg-slate-700' : $page.component === 'Home'}"
                     >Home</Link>
                </div>

                <div v-if="$page.props.auth.user" class="space-x-6 flex">
                    <img :src="$page.props.auth.user.avatar ? ('storage/' + $page.props.auth.user.avatar) : ('storage/default.jpg')" class="avatar" alt="">
                    <Link :href="route('dashboard')" class="nav-link"
                    :class="{'bg-slate-700' : $page.component === 'Dashboard'}"
                    >Dashboard</Link>
                    <Link :href="route('logout')" method="post" as="button" class="nav-link">Logout</Link>
                </div>
                <div v-else class="space-x-6">
                    <Link :href="route('register')" class="nav-link"
                    :class="{'bg-slate-700' : $page.component === 'Auth/Register'}"
                    >Register</Link>
                    <Link :href="route('login')" class="nav-link"
                    :class="{'bg-slate-700' : $page.component === 'Auth/Login'}"
                    >Login</Link>
                </div>
            </nav>
        </header>

        <main class="p-4">
            <slot />
        </main>
    </div>
</template>