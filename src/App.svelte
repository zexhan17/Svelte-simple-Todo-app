<script>
	let todos = [
		{ done: false, text: 'finish Svelte tutorial' },
		{ done: false, text: 'build an app' },
		{ done: false, text: 'world domination' }
	];

	function add() {
		todos = todos.concat({ done: false, text: '' });
	}

	function clear() {
		todos = todos.filter(t => !t.done);
	}

	$: remaining = todos.filter(t => !t.done).length;
</script>

<div class="main">

<h1>Todos</h1>


{#each todos as todo}
	<div class:done={todo.done}>
		<input
			type=checkbox
			bind:checked={todo.done}>
		<input
			placeholder="What needs to be done?"
			bind:value={todo.text}>
	</div>
{/each}

<h3>{remaining} remaining</h3>
	
<button on:click={add}>
	Add new
</button>

<button on:click={clear}>
	Remove completed
</button>

</div>

<style>
	.done {
		opacity: 0.4;
	}
	.main{
		margin-left: 40%;
	}
	button {
		margin-top: 10px;
		margin-left: 10px;
	}
</style>