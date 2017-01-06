---
title:  "Build  your own cdh-spark and run in cluster"
date:   2016-01-08 13:44:16
categories: jekyll update
---

1.下载CDH版本的spark

	https://github.com/cloudera/spark/tree/cdh5-1.6.0_5.7.0

2.二次修改后用maven打包编译
{% highlight ruby %}

export MAVEN_OPTS="-Xmx2g -XX:ReservedCodeCacheSize=512m -XX:MaxPermSize=512M"

./build/mvn -Pyarn -Phadoop-2.6 -Dhadoop.version=2.6.0-cdh5.7.0 -DskipTests clean package

{% endhighlight %}

3.修改spark-default.conf文件
    修改spark-default.conf文件的  spark.yarn.jar属性为 自己开发的spark包，就可以在集群上跑自己二次开发的spark（Mllib  GraphX等）

4.spark-submit时 必须需要设置deploy-mode 为cluster

