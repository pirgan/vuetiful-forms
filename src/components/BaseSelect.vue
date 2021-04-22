<template>
	<div class="form-group">
		<label>{{ label }}</label>
		<select class="form-control" v-on:change="$emit('input', $event.target.value)">
			<option 
				v-for="option in options" 
				v-bind:key="option.value" 
				v-bind:value="option.value" 
				v-bind:selected="value === option.value">
					{{option.label || 'No label'}}
			</option>
		</select>
	</div>
</template>

<script>
export default {
	props: {
		label: {
			type: String,
			required: true
		},
		options: {
			type: Array,
			required: true,
			validator(options) {
				return !options.find(options => typeof options !== 'object')
			}
		},
		value: {
			type: String,
			required: true
		}
	}
}
</script>

<style scoped>
</style>