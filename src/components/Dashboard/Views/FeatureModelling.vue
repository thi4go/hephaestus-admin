<template>
  <div class="card">
    <div class="header">
      <h4 class="title">Models</h4>
      <p class="category">List of Feature Models you can choose from</p>
      <br /><br />
      <div class="col-md-3">
        <button :class="selected == 1 ? 'btn btn-default btn-block active' : 'btn btn-default btn-block'"
                @click="selectModel(1)"> Iris Email Client
        </button>
      </div>
      <div class="col-md-3">
        <button :class="selected == 2 ? 'btn btn-default btn-block active' : 'btn btn-default btn-block'"
                @click="selectModel(2)"> Smartphone Firmware
      </button>
      </div>
    </div>
    <br /><br />
    <br /><br />
    <div class="content">
      <div class="row">

        <div class="col-md-6">
          <h5>Feature Selection</h5>
          <el-tree
            :data="data3"
            :props="defaultProps"
            show-checkbox
            default-expand-all
            @check-change="handleCheckChange">
          </el-tree>
          <br /><br /><br />
          <div class="col-md-12">

            <el-button round @click="generateJson">Tree to JSON</el-button>
          </div>
        </div>

        <div class="col-md-6">
          <h5>Generated JSON</h5>
          <!-- <div class="alert alert-info">
            <button type="button" aria-hidden="true" class="close">×</button>
            <span>
              <b> Info - </b> This is a regular notification made with ".alert-info"</span>
          </div>
          <div class="alert alert-success">
            <button type="button" aria-hidden="true" class="close">×</button>
            <span>
              <b> Success - </b> This is a regular notification made with ".alert-success"</span>
          </div>
          <div class="alert alert-warning">
            <button type="button" aria-hidden="true" class="close">×</button>
            <span>
              <b> Warning - </b> This is a regular notification made with ".alert-warning"</span>
          </div>
          <div class="alert alert-danger">
            <button type="button" aria-hidden="true" class="close">×</button>
            <span>
              <b> Danger - </b> This is a regular notification made with ".alert-danger"</span>
          </div> -->
        </div>

      </div>

      <br>
      <br>
      <br /><br /><br /><br /><br />
      <!-- <div class="places-buttons">
        <div class="row">
          <div class="col-md-9">
            <h5>Notifications Places
              <p class="category">Click to view notifications</p>
            </h5>
          </div>
        </div>
        <div class="row">
          <div class="col-md-3">
            <button class="btn btn-default btn-block" @click="notifyVue('top', 'left')">Top Left</button>
          </div>
          <div class="col-md-3">
            <button class="btn btn-default btn-block" @click="notifyVue('top', 'center')">Top Center</button>
          </div>
          <div class="col-md-3">
            <button class="btn btn-default btn-block" @click="notifyVue('top', 'right')">Top Right</button>
          </div>
        </div>
        <div class="row">
          <div class="col-md-3">
            <button class="btn btn-default btn-block" @click="notifyVue('bottom', 'left')">Bottom Left</button>
          </div>
          <div class="col-md-3">
            <button class="btn btn-default btn-block" @click="notifyVue('bottom', 'center')">Bottom Center</button>
          </div>
          <div class="col-md-3">
            <button class="btn btn-default btn-block" @click="notifyVue('bottom', 'right')">Bottom Right</button>
          </div>

        </div>
      </div> -->
    </div>
  </div>
</template>
<script>
  import PaperNotification from 'src/components/UIComponents/NotificationPlugin/Notification.vue'

  export default {

    data () {
      return {
        selected: 0,
        data3: [{
          id: 1,
          label: 'Iris',
          children: [{
            id: 3,
            label: 'Security',
            children: [{
              id: 4,
              label: 'SHA-256'
            }, {
              id: 5,
              label: 'RSA'
              // disabled: true
            }]
          }, {
            id: 2,
            label: 'Persist',
            children: [{
              id: 6,
              label: 'SQL'
            }, {
              id: 7,
              label: 'NoSQL'
              // disabled: true
            }]
          }]
        }],
        defaultProps: {
          children: 'children',
          label: 'label',
          disabled: 'disabled'
        }
      }
    },

    methods: {
      notifyVue (verticalAlign, horizontalAlign) {
        var color = Math.floor((Math.random() * 4) + 1)
        this.$notifications.notify(
          {
            message: 'Welcome to <b>Paper Dashboard</b> - a beautiful freebie for every web developer.',
            icon: 'ti-gift',
            horizontalAlign: horizontalAlign,
            verticalAlign: verticalAlign,
            type: this.type[color]
          })
      },

      selectModel (index) {
        this.selected = index
      },

      generateJson () {
        // let json = {}
      },

      handleCheckChange (data, checked, indeterminate) {
        console.log(data, checked, indeterminate)
      },

      handleNodeClick (data) {
        console.log(data)
      }

    },

    components: {
      PaperNotification
    }

  }

</script>
<style>

</style>
