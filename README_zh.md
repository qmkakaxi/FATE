[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![CodeStyle](https://img.shields.io/badge/Check%20Style-Google-brightgreen)](https://checkstyle.sourceforge.io/google_style.html) [![Pinpoint Satellite](https://img.shields.io/endpoint?url=https%3A%2F%2Fscan.sbrella.com%2Fadmin%2Fapi%2Fv1%2Fpinpoint%2Fshield%2FFederatedAI%2FFATE)](https://github.com/mmyjona/FATE-Serving/pulls) [![Style](https://img.shields.io/badge/Check%20Style-Black-black)](https://checkstyle.sourceforge.io/google_style.html)

<div align="center">
  <img src="./doc/images/FATE_logo.png">
</div>

[DOC](./doc) | [Quick Start](./examples/federatedml-1.x-examples) | [English](./README.md)

FATE (Federated AI Technology Enabler) 是微众银行AI部门发起的开源项目，为联邦学习生态系统提供了可靠的安全计算框架。FATE项目使用多方安全计算 (MPC) 以及同态加密 (HE) 技术构建底层安全计算协议，以此支持不同种类的机器学习的安全计算，包括逻辑回归、基于树的算法、深度学习和迁移学习等。

FATE官方网站：<https://fate.fedai.org/>

## 参与到FATE开源社区

*  加入我们的邮件列表 [Fate-FedAI Group IO](https://groups.io/g/Fate-FedAI)，您可以提出问题或参与讨论。

*  对于常见问题, 我们为您提供了 [FAQ文档](https://github.com/WeBankFinTech/FATE/wiki)。

*  请使用 [issues](https://github.com/WeBankFinTech/FATE/issues) 提交BUG。

*  请使用 [pull requests](https://github.com/WeBankFinTech/FATE/pulls) 提交、贡献代码。


## FATE中的联邦学习算法

FATE目前支持三种联邦学习算法：横向联邦学习、纵向联邦学习以及迁移学习。算法细节请参考文档 [federatedml](./federatedml) 。


## 安装教程

FATE支持Linux或Mac操作系统，并根据不同的应用场景分为单机部署以及集群部署。

运行环境: jdk1.8+、Python3.6、python virtualenv、mysql5.6+、redis-5.0.2

#### 单机部署

FATE为开发人员提供了单机部署架构版本。单机部署版本可以帮助开发人员快速开发以及测试FATE。该版本支持两种类型：1）Docker；2）手动编译。

具体细节请参阅单机部署指南：[standalone-deploy](./standalone-deploy/)。

#### 集群部署

FATE同样为大数据场景提供了分布式运行部署架构版本。从单机部署迁移到集群部署仅需要更改配置文件，不需要更改算法。

具体细节请参阅集群部署指南：[cluster-deploy](./cluster-deploy)。

## 运行测试

./federatedml/test 文件夹中提供了所有单元测试的脚本。

安装FATE后，可以使用以下命令运行测试：

> sh ./federatedml/test/run_test.sh

如果FATE被正确安装，那么所有单元测试都将成功通过。

## 示例程序

### 快速开始

我们提供了一个用于快速搭建训练任务的python脚本作为示例。该脚本位于：["./examples/federatedml-1.x-examples"](./examples/federatedml-1.x-examples)

#### 单机部署版本
1. 启动单机部署版本的 hetero-lr 任务 (默认)
> python quick_run.py


#### 集群版本

1. Host party:
> python quick_run.py -r host

2. Guest party:
> python quick_run.py -r guest

生成的配置文件存储在名为 **user_config** 的新创建的文件夹中

#### 启动预测任务

一旦完成训练任务，就可以开始相应的预测任务。您需要将quick_run.py脚本中的“ TASK”变量修改为“ predict”：
```
# 定义任务类型
# TASK = 'train'
TASK = 'predict'
```
然后，您需要做的就是运行以下命令：
> python quick_run.py

请注意，仅当您完成训练任务后，执行此命令才有效。

###  获取模型并检查结果
FATE提供了名为 fate-flow 的工具用来跟踪组件输出模型或日志。fate-flow的部署和使用可以在 [这里](./fate_flow/README.md) 找到。


## 文档资料
### API 文档
FATE在 [doc-api](./doc/api/) 文件夹中提供了API文档，包括 federatedml, eggroll, federation.
### 开发者文档
如何使用FATE开发联邦学习算法？您可以在 [develop-guide](./doc/develop_guide.md) 中查看FATE开发指南。

### 其他文档
FATE还在 [doc](./doc/) 中提供了许多其他文档。这些文档可以帮助您更好地了解FATE。
### License
[Apache License 2.0](LICENSE)