<template>
    <h2>{{counterTitle}}</h2>
    <p>{{ count }} <sub>2</sub> = {{ getComputedMessageData }}</p>
    <div>
        <button class="addbtn" @click="increase">+1</button>
        <button class="popbtn" @click="decrease">-1</button>
    </div>
</template>

<script>

export default {
    props: {
        title: {
            type: String,
            required: true
        },
        start:{
            type: Number,
            default: 67,
            validator(value){
                return value >= 0
            }
        }
    },
    name: 'Counter',
    data() {
        return {
            count: this.start
        }
    },
    methods: {
        getMessageData() {
            console.log('getMessageData() called');
            return this.count * this.count
        },
        increase() {
            this.count++;
        },
        decrease() {
            this.count--;
        }
    },
    computed: {
        getComputedMessageData() {
            console.log('Computed getMessageData() called');
            return this.count * this.count
        },
        counterTitle() {
            return this.title || 'Default Title'
        }
    }

}
</script>

<style>
.addbtn {
    background-color: #25c3c3;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 8px;
}

.popbtn {
    background-color: #f44336;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 8px;
}
</style>