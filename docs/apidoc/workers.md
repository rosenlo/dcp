<!-- vim-markdown-toc GFM -->

* [基础信息](#基础信息)
* [API](#api)
    * [应用服务扩容分析](#应用服务扩容分析)

<!-- vim-markdown-toc -->


## 基础信息

环境  |模块          |地址                      |说明        |
------|--------------|--------------------------|------------|
PROD  |APIServer     |http://localhost:30200    | k8s proxy  |
PROD  |Collector     |tcp://localhost:40002     | local pod  |
PROD  |Rules         |tcp://localhost:40003     | local pod  |
PROD  |Workers       |tcp://localhost:40004     | local pod  |


## API

### 应用服务扩容分析

- GET /api/v1/workers/analyzing

- 功能说明：
    - 应用服务当前 CPU 利用率是否满足扩容条件

- URL Query:

名称    |  类型   | 必填  | 默认值  | 说明   |
--------|---------|-------|---------|--------|
app_name|string   |是     |无       |应用名  |
cluster |string   |是     |无       |集群名  |
priority|string   |是     |无       |应用等级，如0、1、2 详情参考[服务分级]()|

- Response

```json
{
    "error_message": "no need to scaling",
    "error_code": 1104000,
    "result": false
}
```

- Response 字段说明


名称         |  类型   | 说明                                 |
-------------|---------|--------------------------------------|
error_message|string   |请求失败返回的错误信息                |
error_code   |int      |错误编码， 0 表示成功，>0 表示失败错误|
result       |bool     |请求是否成功                          |

