<!-- markdownlint-disable MD033 -->
<h1 align="center">
    <img src="./docs/assets/icon_kubedoop.png" alt="Kubedoop Logo" width="150">
  <br>
  Kubedoop Data Platform
</h1>
<div align="center">

[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![EN doc](https://img.shields.io/badge/Docs-English-blue.svg)](https://kubedoop.dev/docs/)
[![CN doc](https://img.shields.io/badge/文档-中文版-blue.svg)](https://kubedoop.dev/zh/docs/)

</div>

Kubedoop Data Platform is a modular open-source data platform that provides Kubernetes-native deployment
and management of popular open source data apps like Apache Kafka, Apache Doris, Trino and Apache Spark. All data apps work together seamlessly, and can be added or removed in no time.
Based on Kubernetes, it allows you to deploy, scale and manage data infrastructure in any environment running everywhere – on-prem or in the cloud.

You can declaratively build these environments, and we don’t stop at the tool level as we also provide ways for the users to interact with the platform in the "as Code"-approach.

## Features

* **Roles and role groups**: Different processes have different tasks that they need to fulfill, which in turn have different configuration settings that only apply to that task.
For example coordination, storage, logging and processing tasks require different amounts of threads, memory and storage capacity. These different settings can be put in the per role configuration spec.
The roles or processes are often replicated multiple times. These replicas can further be subdivided into role groups. Roles and role groups are defined in the resource manifest.
* **Service discovery ConfigMap**: This ConfigMap has the same name as the product instance and contains information about how to connect to the  instance.
The ConfigMap is used by other Operators to connect products together and can also be used by you, the user, to connect external software to Kubedoop-operated software.
* **Product image selection**: Uses the publicly available Images from the Image registry hosted by Kubedoop.
Custom docker registries can be used to fetch the image from a local image registry rather than from the internet.
Custom images allows to provide self-hosted or user-created images (e.g. user extended Kubedoop images)
* **Overrides**: The resource definitions of all products support overrides, specifically for the product configuration, environment variables, and the PodSpec the operators generate.
The cluster definitions also supports overriding configuration aspects, either per role or per role group, where the more specific override (role group) has precedence over the less specific one (role).
* **Authentication**: Uses the AuthenticationClass as a central mechanism to handle user authentication across supported products.
The authentication mechanism needs to be configured only in the AuthenticationClass which is then referenced in the product. Multiple different authentication providers are supported.
* **Logging**: Logging is important for observability of the platform. Kubedoop provides human-readable plaintext logs for each running container,
as well as aggregated and persisted logs with identical structure across the whole platform. Log levels can be set for individual modules and configuration
is identical across all products, but custom logging configuration files can be supplied as well.
* **S3 resources**: Uses S3Connection and S3Bucket objects to configure access to S3 storage. An S3Connection object contains information such as the host name of the S3 server, it’s port,
TLS parameters and access credentials. An S3Bucket contains the name of the bucket and a reference to an S3Connection,
the connection to the server where the bucket is located. An S3Connection can be referenced by multiple buckets.
* **TLS server verification**: A TLS section is part of Kubedoop CRDs and describes how to connect to a TLS enabled system like LDAP or S3.


All this makes Kubedoop Data Platform an ideal tool for scenarios including modern Data Warehouses, Data Lakehouses, Event Streaming, Machine Learning or Data Meshes.
Use it to create unique and enterprise-class data architectures.

## Architecture

TODO

## Getting Started

* [Introduction](https://kubedoop.io/docs)
* [Installation](https://kubedoop.io/docs/install)
* [Deploy Your Application](https://kubedoop.io/docs/quick-start)

## Supported product versions

| Product                       | Version                                               |
|-------------------------------|-------------------------------------------------------|
| [Apache Airflow](https://github.com/zncdatadev/airflow-operator)                | 2.9.3, 2.10.2                                         |
| [Apache DolphinScheduler](https://github.com/zncdatadev/dolphinscheduler-operator)       | 3.2.2                                                 |
| [Apache Doris](https://github.com/zncdatadev/doris-operator)                  | 2.1.7                                                 |
| [Apache Hadoop HDFS](https://github.com/zncdatadev/hdfs-operator)            | 3.3.4, 3.3.6, 3.4.0                                   |
| [Apache HBase](https://github.com/zncdatadev/hbase-operator)                  | 2.4.18, 2.6.0                                         |
| [Apache Hive](https://github.com/zncdatadev/hive-operator)                   | 3.1.3, 4.0.0                                          |
| [Apache Kafka](https://github.com/zncdatadev/kafka-operator)                  | 3.7.1                                                 |
| [Apache Kyuubi](https://github.com/zncdatadev/kyuubi-operator)                 | 1.9.3                                                 |
| [Apache Nifi](https://github.com/zncdatadev/nifi-operator)                   | 1.27.0, 2.0.0                                         |
| [Apache Spark](https://github.com/zncdatadev/spark-k8s-operator)                  | 3.5.1                                                 |
| [Apache Superset](https://github.com/zncdatadev/superset-operator)               | 3.1.3, 4.0.2                                          |
| [Trino](https://github.com/zncdatadev/trino-operator)                         | 451                                                   |
| [Apache Zookeeper](https://github.com/zncdatadev/zookeeper-operator)              | 3.8.4, 3.9.2                                          |

## Supported Platforms

We develop and test our operators on the following cloud platforms:

* Kubernetes 1.26+
* K3s
* MicroK8s
* Kind
* MiniKube

  
## Contributing

If you'd like to contribute to Kubedoop, please refer to our [Contributing Guide](https://kubedoop.dev/docs/developer-manual/collaboration) for more information.
We welcome contributions of all kinds, including but not limited to code, documentation, and use cases.

## License

Copyright 2024.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
