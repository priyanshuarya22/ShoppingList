/* eslint-disable */
<template>
    <div class="input-group">
        <input @keyup.enter="addItem" v-model="newItem" placeholder="add shopping list item" type="text" class="form-control">
        <span class="input-group-btn">
            <button @click="addItem" class="btn btn-default" type="button">Add!</button>
        </span>
    </div>
</template>

<script>
export default {
    props: ['id'],
    data () {
        return {
            newItem: ''
        }
    },
    methods: {
        addItem () {
            var text;

            text = this.newItem.trim();
            if (text) {
                this.$emit('add', this.newItem)
                this.newItem = ''
                this.$store.dispatch('updateList', this.id)
            }
        }
    }
}
</script>

<style scoped>
</style>
