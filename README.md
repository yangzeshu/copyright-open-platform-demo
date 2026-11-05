# 版权开放平台 Demo

短剧生产方开放合作平台的交互演示（纯静态 HTML + 原生 JS/CSS，无构建、无依赖）。

- **C 端（内容合作方）**：注册/登录 → 资质认证 → 签署授权入驻合同 → 收益明细 → 个人中心
- **B 端（运营后台）**：主体认证 → 合同列表 → 系统配置（人员配置）

> 全部为演示数据，不含真实业务数据；刷新页面即回到初始状态。

## 在线预览

- 入口：<https://yangzeshu.github.io/copyright-open-platform-demo/>
- 运营后台：<https://yangzeshu.github.io/copyright-open-platform-demo/B端/accounts.html>
- 页面右上角「运营后台 / 内容合作方」可双向切换

## 本地预览

直接双击 `index.html` 即可（也可起任意静态服务器，如 `python -m http.server`）。

## 页面结构

```
index.html              入口（= login.html，登录/注册）
workbench.html          工作台
workbench-cert.html     资质认证
workbench-contract.html 合同签署
contracts.html          合同管理
earnings.html           收益管理（收益明细）
profile.html            个人中心
B端/
  accounts.html         主体认证
  contracts.html        合同列表
  personnel.html        人员配置
```

## 关键业务规则（演示口径）

- **认证**：仅企业一种类型，拆「国内主体信息」（国内公司名称、营业执照、商务）与「海外主体信息」（海外公司全称、联系人、银行与地址信息等）
- **合同**：单次签署两份模板（合作框架协议 + 保密协议），合同类型统一为「授权入驻合同」，命名为 `{主体名称} 授权入驻合同`；8 个乙方字段全部读取自认证信息、不可修改；审核通过前需填写甲方信息（联系人 / 联系电话 / 联系邮箱 / 合作期限）
- **手动上传**：运营可为已认证主体手动补充已签署合同，支持 e签宝合同与线下 PDF 两种方式
- **人员配置**：用户由内部系统同步（不可自建），维护真实姓名、手机号、邮箱、角色（商务 / 商务组长）、组别（国内 / 国外）

## 技术说明

- 每页自包含内联 CSS/JS，高仿 Ant Design 视觉，品牌主色 `#ff2e63`
- 无框架、无 CDN、无后端；所有交互在内存中完成
