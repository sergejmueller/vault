<script>
    import { HOME_URL } from './Constants';
    import { tooltip } from './Helpers';
    import { createEventDispatcher } from 'svelte';

    export let isUnlocked;

    const dispatch = createEventDispatcher();

    const add = () => dispatch('add', true);
    const lock = () => dispatch('lock', {seed: null});
    const search = event => dispatch('search', event.target.value.trim());
</script>

<style>
    header {
        height: 64px;
        display: flex;
    }

    a {
        height: 32px;
        display: flex;
        align-items: center;
        flex-wrap: nowrap;
    }
    a h1 {
        margin-left: 10px;

        color: var(--color-header-slogan);
        font-size: 20px;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    input {
        height: 32px;
        padding: 0 8px;
        margin-left: auto;
        background: var(--color-header-search);
        border-radius: 3px;

        font-size: 14px;
        -webkit-appearance: textfield;
    }
    input::placeholder {
        color: var(--color-header-placeholder);
    }

    nav {
        display: flex;
    }

    nav a,
    nav button {
        width: 32px;
        height: 32px;
        margin-left: 8px;
        border-radius: 3px;
        display: flex;
        align-items: center;
        justify-content: center;
        background: var(--color-grey);

        color: var(--color-white);
        font-size: 18px;
    }
    nav button:first-of-type {
        margin-left: 16px;
        background: var(--color-blue);
    }

    nav button span {
        width: 1px;
        height: 14px;
        background: var(--color-white);
    }
    nav button span:last-child {
        margin-left: -1px;
        transform: rotate(90deg);
    }

    nav button svg {
        fill: var(--color-white);
        display: block;
    }

    @media (max-width: 537px) {
        header {
            height: 96px;
            flex-wrap: wrap;
        }

        input {
            width: 100%;
            order: 2;
            margin: 16px 0 -16px;
            flex-basis: 100%;
        }

        nav {
            margin-left: auto;
        }
    }
</style>

<header class="container">
    <a href="{HOME_URL}">
        <svg width="32" height="32" viewBox="0 0 95 95">
            <g fill="none" fill-rule="evenodd" transform="translate(.125 .734375)">
                <path d="m93.7128926 46.9016875c0 25.835834-20.9439278 46.7807441-46.7807442 46.7807441-25.835832 0-46.78074254-20.9439296-46.78074254-46.7807441 0-25.835832 20.94392814-46.78074336 46.78074254-46.78074336 25.835834 0 46.7807442 20.94392886 46.7807442 46.78074336" id="icon-vault-background"/>
                <path d="m38.3164141 17.5205957c-.2684727 0-10.8203848 6.2590781-11.2292911 6.6634473-.2185253.216705-.1710625.3825468.3338594 1.2138925 5.5741992 9.1793165 9.2862578 15.5175098 9.1592676 15.6303457-.0875801.0779493-3.4466875.0389766-7.4620742-.085746-4.0153906-.1247227-8.2296192-.2373633-9.3651621-.244961h-2.0644453l-.1001446 6.7033945c-.0617148 3.9384747-.0391855 6.7692657.0558731 6.8686524.1523847.16175 11.8685312-.1032852 16.6825566-.3761133 1.6596367-.093541 2.0151211-.0662578 2.0978379.1520039.0567129.1520059-.6956562 1.5940996-1.7472695 3.3518926-1.0160352 1.6979707-3.1900157 5.3310723-4.8300449 8.0714375-1.6400137 2.7407578-2.9438457 5.0802617-2.899125 5.1985547.1152714.3059551 10.8130625 6.5775019 11.2404042 6.5899746.3292754 0 2.7678497-4.4172852 8.3357168-15.1289219.4171778-.8025058.876168-1.4590508 1.0183106-1.4590508.1580644 0 1.7983418 2.9418711 4.2235059 7.5700176 5.01283 9.5663418 4.874246 9.3026719 4.9691523 9.3026719.0442168 0 1.2208477-.6875274 2.6153437-1.5216035 1.394502-.8346582 3.9541739-2.3580196 5.692545-3.3918418 1.7383691-1.0338262 3.1606699-1.955791 3.1606699-2.0466035 0-.0915918-1.6562441-2.9325196-3.6837344-6.3157852-2.0274902-3.3836601-4.2249765-7.0535918-4.8856855-8.1571836-.6751426-1.1277539-1.1381524-2.0773926-1.0517051-2.1660625.0865664-.0896426 4.1914258-.0389746 9.3874199.1130293 5.0764863.1520039 9.2990352.2167031 9.3818477.1364141.2014121-.1929278.3208476-13.4636992.1224414-13.5893926-.0853946-.0545664-3.9501914.025332-8.5861231.1773379-10.0739121.3271992-10.3.3295371-10.3.0857461 0-.1052363 1.6191016-2.8752246 3.5947071-6.1561797 5.8988339-9.7968828 6.1922656-10.3006426 6.1098886-10.43725-.0433593-.0740547-1.0626953-.7037051-2.2647773-1.4081856-1.2020723-.7044824-3.7217988-2.1964648-5.6035137-3.3115527-1.8816992-1.1148945-3.4965019-2.023416-3.5891348-2.023416-.1501914 0-3.7411191 6.6342168-7.6178867 14.0851621-.9171679 1.7626699-1.4886445 2.6746953-1.6582422 2.644877-.1423769-.0253301-2.2257109-3.796795-4.6297128-8.3849922-2.4890723-4.75092-4.4737774-8.3440703-4.6130196-8.3450469z" fill="#fff" fill-rule="nonzero" id="icon-vault-gear"/>
            </g>
        </svg>
        <h1>
            Vault
        </h1>
    </a>

    {#if isUnlocked}
        <input type="search" on:keyup={search} on:change={search} on:search={search} placeholder="Instant Search">

        <nav>
            <button on:click={add} use:tooltip="{'New Item'}">
                <span></span>
                <span></span>
            </button>

            <button on:click="{lock}" use:tooltip="{'Lock Vault'}">
                <svg width="16" height="16">
                    <use xlink:href="#icon-lock" />
                </svg>
            </button>

            <a href="https://siasky.net/AACJOu5-oSfCV3suwty187btkQyzFZIX9hy7UfZU0s_EEQ" target="_blank" rel="noopener" use:tooltip="{'User Guide'}">?</a>
        </nav>
    {/if}
</header>
