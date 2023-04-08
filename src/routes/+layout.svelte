<script lang="ts">
	import '../app.postcss';
	import { onMount } from 'svelte';
	import {
		DarkMode,
		Navbar,
		NavBrand,
		NavLi,
		NavUl,
		NavHamburger,
		Button,
		Input
	} from 'flowbite-svelte';
	import {
		Footer,
		FooterBrand,
		FooterLinkGroup,
		FooterLink,
		FooterCopyright,
		FooterIcon
	} from 'flowbite-svelte';
	import '@fontsource/poppins';

	let active = 0;

	function setActive(index: number) {
		active = index;
	}

	let breakPoint: number = 1024;
	let width: number;
	let activateClickOutside = true;
	let drawerHidden: boolean = false;
	$: if (width >= breakPoint) {
		drawerHidden = false;
		activateClickOutside = false;
	} else {
		drawerHidden = true;
		activateClickOutside = true;
	}
	onMount(() => {
		if (width >= breakPoint) {
			drawerHidden = false;
			activateClickOutside = false;
		} else {
			drawerHidden = true;
			activateClickOutside = true;
		}
	});
	let darkmodebtn =
		'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 focus:outline-none focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 rounded-lg text-lg p-2.5  right-2 top-12  md:top-3 md:right-2 z-50';
	let divClass = 'w-full md:block md:w-auto';
	let ulClass =
		'flex flex-col p-4 text-center mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-lg md:font-medium';
</script>

<svelte:window bind:innerWidth={width} />

<header class="sticky shadow-xl dark:shadow-indigo-500/50 top-0 z-50 ">
	<Navbar let:hidden let:toggle class="">
		<NavBrand href="/" class="">
			<img
				src="/images/logos.webp"
				class="h-auto w-9 md:w-9 lg:w-9"
				alt="mission"
			/>
			<span class="self-center whitespace-nowrap text-2xl  dark:text-white ">
				<p class="text-2xl">Asterisc.in</p>
			</span>
		</NavBrand>
		<div class="flex md:order-2">
			<!-- <a href="#getstarted" class="mt-1" ><Button size="sm" >Get started</Button></a> -->
			
			<DarkMode class="ml-2" btnClass={darkmodebtn} />
			<NavHamburger on:click={toggle} />
		</div>

		<NavUl {hidden} {divClass} {ulClass}>
			<NavLi href="/" active={active === 0} on:click={() => setActive(0)}><p class=" text-base  md:text-xl">Home</p></NavLi>
			<NavLi href="/aboutus" active={active === 1} on:click={() => setActive(1)}><p class="text-base md:text-xl">About Us</p></NavLi>
			<NavLi href="/courses" active={active === 2} on:click={() => setActive(2)}><p class="text-base md:text-xl">Courses</p></NavLi>
			<NavLi href="/faqs" active={active === 3} on:click={() => setActive(3)}><p class="text-base md:text-xl">FAQ</p></NavLi>
			<NavLi href="/testimonials" active={active === 4} on:click={() => setActive(4)}
				><p class="text-base md:text-xl">Testimonials</p></NavLi
			>
			<NavLi href="https://astr-one.vercel.app/" active={active === 5} on:click={() => setActive(5)}><p class="text-base md:text-xl">Projects</p></NavLi>
		</NavUl>
	</Navbar>
</header>

<main>
	<slot />
</main>

<Footer footerType="socialmedia">
	<div class="mx-auto max-w-screen-xl text-center">
		<FooterBrand
			href="https://asterisc.in"
			src="/images/logos.webp"
			alt="Asterisc Logo"
			name="Asterisc.in"
			aClass="flex justify-center items-center text-2xl font-semibold text-gray-900 dark:text-white"
		/>
		
		<p class="my-6 text-gray-500 dark:text-gray-400">
			Join us now for your better tomorrow.
		</p>
		<FooterLinkGroup
			ulClass="flex flex-wrap justify-center items-center mb-6 text-gray-900 dark:text-white"
		>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">About Us</FooterLink>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">FAQs</FooterLink>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">Testimonials</FooterLink
			>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="https://astr-one.vercel.app/">Projects</FooterLink>

			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">Contact Us</FooterLink>
		</FooterLinkGroup>
		<span class="text-sm text-gray-500 sm:text-center dark:text-gray-400"
			>© 2021-2023 <a href="https://asterisc.in/" class="hover:underline">Asterisc.in™ </a>.
			Developed by Asterisc Technocrat Pvt. Ltd. All Rights Reserved.</span
		>
	</div>
</Footer>
<style>
	

	p {
		font-family: "Poppins", sans-serif;
	}
</style>
