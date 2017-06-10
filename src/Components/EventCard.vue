<template>
    <div>
        <div class="panel no-margin" :class="[event.color]" @click="showEventDetails">
            <div class="panel-heading event-title" :class="{'clickable-event':isDaySelected}">{{event.title}}</div>
        </div>

        <EventDetails :show.sync="displayEventDetails" :event="event"></EventDetails>
    </div>
</template>

<script>
    export default {
        components: {
            'EventDetails': require('./EventDetails.vue'),
        },
        data() {
            return {
                displayEventDetails:  false,
            }
        },
        props: {
            event: {
                type: Object
            },
            isDaySelected: {
                type: Boolean
            }
        },
        methods: {
            showEventDetails() {
                if(this.isDaySelected){
                    this.displayEventDetails = true;
                }
            }
        },
    }
</script>
<style>
    .event-title {
        padding: 0px 5px;
        font-size: 12px
    }
    .clickable-event {
        text-decoration: underline;
    }
</style>