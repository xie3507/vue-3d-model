<template>
    <demo-block :vue-code="code" :html-code="htmlCode">
        <template slot="preview">
            <model-collada :backgroundAlpha="0"
                @on-load="onLoad"
                src="static/models/collada/elf/elf.dae"></model-collada>
            <div class="example-loading" v-show="loading"></div>
        </template>
    </demo-block>
</template>

<script>
import DemoBlock from '../components/demo-block';
import ModelCollada from '../../src/model-collada.vue'

const code = `
<template>
    <model-collada src="static/models/collada/elf.dae"></model-collada>
</template>

<script>
    import { ModelCollada } from 'vue-3d-model'

    export default {
        components: {
            ModelCollada
        }
    }
<\/script>
`

const htmlCode = `
<body>
    <div id="app">
        <model-collada src="static/models/collada/elf.dae"></model-collada>
    </div>
    #scripts#
    <script>
        new Vue({
            el: '#app'
        })
    <\/script>
</body>
`

export default {
    name: 'demo-collada',
    data () {
    	return {
            code,
            htmlCode,
            loading: true
    	}
    },
    methods: {
        onLoad () {
            this.loading = false;
        }
    },
    components: {
        ModelCollada,
        DemoBlock
    }
}
</script>