<template>
    <div class="serverbutton" :class="{'serverbutton-isHome': isHome, 'serverbutton-hasNotification': hasNotification}">
        <img src="../../assets/discord.svg" v-if="isHome"/>
        <div class="mentions" v-if="mentions">{{ mentions }}</div>
    </div>
</template>

<script>
export default {
    props: {
        selected: Boolean,
        isHome: Boolean,
        hasNotification: Boolean,
        mentions: Number
    }
};
</script>

<style scoped>
.serverbutton {
    display: flex;
    flex-shrink: 0;
    align-items: center;
    justify-content: center;
    width: 48px;
    height: 48px;
    margin-top: 8px;
    /* margin-bottom: 8px; */
    background-color: var(--primary);
    cursor: pointer;
    position: relative;
    border-radius: 50%;
    transition: 0.2s;
}

.serverbutton:active,
.serverbutton:hover {
    border-radius: 16px;
    background-color: var(--discord);
}

.serverbutton-hasNotification::before {
    content: "";
    width: 9px;
    height: 9px;
    position: absolute;
    background-color: var(--white);
    left: -17px;
    top: calc(50% - 4.5px);
    border-radius: 50%;
    display: block;
}

.serverbutton-isHome {
    background-color: var(--rocketseat);
}

.serverbutton-isHome:active,
.serverbutton-isHome:hover {
    border-radius: 16px;
    background-color: var(--rocketseat);
}

.mentions {
    background-color: var(--notification);
    width: auto;
    height: auto;
    padding: 0 4px;
    position: absolute;
    bottom: -4px;
    right: -4px;
    border-radius: 12px;
    border: solid 4px var(--quaternary);
    text-align: right;
    font-size: 13px;
    font-weight: bold;
    color: var(--white);
}

img {
    width: 24px;
    height: 24px;
    color: #fff;
}

</style>