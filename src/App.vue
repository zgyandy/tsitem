
<template>
  <div>
    <!-- <van-address-edit
    :area-list="areaList"
    :address-info="addressInfo"
    show-postal
    show-delete
    show-set-default
    show-search-result
    :search-result="searchResult"
    @save="onSave"
    @delete="onDelete"
    @change-detail="onChangeDetail"
    /> -->
    <div><span>公司名称：</span><input v-model="comName"/></div>
    <div><span>姓名：</span><input v-model="name"/></div>
    <div><span>移动电话：</span><input v-model="phone"/></div>
    <div style="font-size: 14px"><span style="margin-left: 13px">公司地址：</span><input class="addr-input" v-model="province" @click="show" />
      <input class="addr-input" v-model="city" @click="show"/>
      <input class="addr-input" v-model="district" @click="show"/>
      <!-- <van-field
        v-model="street"
        type="text"
        placeholder="街道门牌、楼层房间号等信息"
      /> -->
    </div>
    <div v-show="flag">
      <van-area :area-list="areaList" :item-height=25 @confirm="onAddrConfirm" @cancel="shut" :value="addrCode"/>
    </div>
  </div>
</template>

<script>
import area from '@/assets/js/area.js';
export default {
  data () {
    return {
      comName: {},
      searchResult: '',
      addrCode: '440105',
      province: '',
      city: '',
      district: '',
      street: '',
      companyName: '',
      name: '',
      phone: '',
      address: '',
      areaList: area,
      flag: false,
      addressInfo: ''
      // flag: true
    }
  },
  created () {
    this.init()
  },
  methods: {
    init () {
      // // 初始化地址选择器
      // this.areaList = areaList.areaList // 初始化选择器数据
      // 初始化复选框
      // this.allMajor = this.getMajor()
    },
    show () {
      this.flag = true
    },
    onAddrConfirm (e) { // 点击确认，获取所选的省市区数据
      // 确定选择,返回的必定是三元素数组
      console.log('this.onAddrConfirm=>e', e)
      this.province = e[0].name
      this.city = e[1].name
      this.district = e[2].name
      this.flag = false
    },
    shut () {
      this.flag = false
    },
    onChangeDetail (val) {
      if (val) {
        this.searchResult = [{
          name: '黄龙万科中心',
          address: '杭州市西湖区'
        }]
      } else {
        this.searchResult = []
      }
    },
    onSave (e) {
      console.log(e)
    },
    onDelete (e) {
      console.log(e)
    }
  }
}
</script>
