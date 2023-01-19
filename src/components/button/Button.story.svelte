<script lang="ts">
	import type { Hst } from '@histoire/plugin-svelte';
	import { logEvent } from 'histoire/client';
	import Button from './Button.svelte';

	export let Hst: Hst;

	let disabled = false;
	let content = 'click me 😏';

	function logClick(event: MouseEvent) {
		logEvent('Click', event);
	}
</script>

<Hst.Story>
	<svelte:fragment slot="controls">
		<Hst.Text bind:value={content} title="Content" />
		<Hst.Checkbox bind:value={disabled} title="Disabled" />
	</svelte:fragment>

	<Button on:click={logClick} {disabled}>{content}</Button>

	<!--
    <Hst.Variant title="default"><Button>button</Button></Hst.Variant>
    <Hst.Variant title="Fast"><Button>button 🏎️</Button></Hst.Variant>
    <Hst.Variant title="Slow"><Button>button 🚜</Button></Hst.Variant>
  -->
</Hst.Story>
