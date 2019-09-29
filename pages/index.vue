<template>
  <section class="section">
    <div>

      <cytoscape ref="cy" :config="config">
        <cy-element
          v-for="def in elements"
          :key="`${def.data.id}`"
          :definition="def"
        />
      </cytoscape>

    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'

export default {
  name: 'HomePage',
  components: {
    Card
  },
  data() {
    return {
      elements: [
        { // node a
          data: { id: 'a' }
        }, { // node b
          data: { id: 'b' }
        }, { // edge ab
          data: { id: 'ab', source: 'a', target: 'b' }
        }
      ],
      config: {
        style: [
          {
            selector: 'node',
            style: {
              'background-color': '#666',
              'label': 'data(id)'
            }
          }, {
            selector: 'edge',
            style: {
              'width': 3,
              'line-color': '#ccc',
              'target-arrow-color': '#ccc',
              'target-arrow-shape': 'triangle'
            }
          }
        ],
        layout: {
          name: 'grid',
          rows: 1
        }
      }
    }
  }
}
</script>
