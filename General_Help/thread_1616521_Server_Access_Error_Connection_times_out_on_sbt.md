---
title: "Server Access Error: Connection times out on sbt"
date: 2010-11-08
forum: General Help
---

### Post by kv_flock on 2010-11-08
[SIZE=3]Trying to run sbt update package-dist on Ubuntu, but coming up with the following errors, where it doesn't make the network connection. Any help? I don't understand why I would be having network connection errors, since some of them are downloading successfully...
[/SIZE][SIZE=2]

root@kv-VirtualBox:/usr/bin/twitter-flockdb-6918136# sbt update package-dist
Getting Scala 2.7.7 ...
:: retrieving :: org.scala-tools.sbt#boot-scala
    confs: [default]
    2 artifacts copied, 0 already retrieved (9911kB/452ms)
Getting org.scala-tools.sbt sbt_2.7.7 0.7.4 ...
:: retrieving :: org.scala-tools.sbt#boot-app
    confs: [default]
    15 artifacts copied, 0 already retrieved (4096kB/367ms)
[info] Recompiling plugin definition...
[info]       Source analysis: 1 new/modified, 0 indirectly invalidated, 0 removed.
[info] 
[info] Updating plugins...
[info] downloading [http://maven.twttr.com/com/twitter/standard-project/0.7.11/standard-project-0.7.11.jar](http://maven.twttr.com/com/twitter/standard-project/0.7.11/standard-project-0.7.11.jar) ...
[info]     [SUCCESSFUL ] com.twitter#standard-project;0.7.11!standard-project.jar (124ms)
[info] downloading [http://maven.twttr.com/ivysvn/ivysvn/2.1.0/ivysvn-2.1.0.jar](http://maven.twttr.com/ivysvn/ivysvn/2.1.0/ivysvn-2.1.0.jar) ...
[info]     [SUCCESSFUL ] ivysvn#ivysvn;2.1.0!ivysvn.jar (3359ms)
[info] :: retrieving :: plugin-definition#plugin-definition_2.7.7 [sync]
[info]     confs: [compile, runtime, test, provided, system, optional, sources, javadoc]
[info]     2 artifacts copied, 0 already retrieved (2996kB/97ms)
[success] Plugins updated successfully.
[info] 
[info]     Extracted source plugin ./lib_managed/scala_2.7.7/standard-project-0.7.11.jar ...
[info] Recompiling plugin...
[info]       Source analysis: 13 new/modified, 0 indirectly invalidated, 0 removed.
[info] Recompiling project definition...
[info]       Source analysis: 1 new/modified, 0 indirectly invalidated, 0 removed.
[info] Standard project rules 0.7.10 loaded (2010-10-12).
[warn] No .svnrepo file; no svn repo will be configured.
[info] Building project flockdb 1.4.6-SNAPSHOT against Scala 2.7.7
[info]    using FlockDBProject with sbt 0.7.4 and Scala 2.7.7
[info] 
[info] == update ==
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/gizzard/1.4.10/gizzard-1.4.10-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/gizzard/1.4.10/gizzard-1.4.10-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/slf4j/slf4j-parent/1.5.2/slf4j-parent-1.5.2.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/slf4j/slf4j-jdk14/1.5.2/slf4j-jdk14-1.5.2-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/slf4j/slf4j-api/1.5.2/slf4j-api-1.5.2-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/configgy/1.6.8/configgy-1.6.8-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/configgy/1.6.8/configgy-1.6.8-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/ostrich/1.2.7/ostrich-1.2.7-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/ostrich/1.2.7/ostrich-1.2.7-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/scala-tools/testing/specs/1.6.2.1/specs-1.6.2.1-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/asm/asm/1.5.3/asm-1.5.3-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/asm/asm/1.5.3/asm-1.5.3-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/cglib/cglib/2.1_3/cglib-2.1_3-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/objenesis/objenesis-parent/1.1/objenesis-parent-1.1.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/commons-logging/commons-logging/1.1/commons-logging-1.1-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/log4j/log4j/1.2.12/log4j-1.2.12-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/log4j/log4j/1.2.12/log4j-1.2.12-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/logkit/logkit/1.0.1/logkit-1.0.1-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/avalon-framework/avalon-framework/4.1.3/avalon-framework-4.1.3-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/avalon-framework/avalon-framework/4.1.3/avalon-framework-4.1.3-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/javax/servlet/servlet-api/2.3/servlet-api-2.3-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/mockito/mockito-core/1.8.1/mockito-core-1.8.1-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-parent/1.1/hamcrest-parent-1.1.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-core/1.1/hamcrest-core-1.1-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-all/1.1/hamcrest-all-1.1-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar
[warn]     module not found: org.jboss.netty#netty;3.1.5.GA
[warn] ==== local: tried
[warn]   /root/.ivy2/local/org.jboss.netty/netty/3.1.5.GA/ivys/ivy.xml
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   /root/.ivy2/local/org.jboss.netty/netty/3.1.5.GA/jars/netty.jar
[warn] ==== powermock-api: tried
[warn]   [http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== download.java.net: tried
[warn]   [http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== localm2: tried
[warn]   /root/.ivy2/local/org/jboss/netty/netty/3.1.5.GA/ivy-3.1.5.GA.xml
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   /root/.ivy2/local/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar
[warn] ==== testing.scala-tools.org: tried
[warn]   [http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== public: tried
[warn]   [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== ibiblio: tried
[warn]   [http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== local-libs: tried
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   /usr/bin/twitter-flockdb-6918136/libs/netty-3.1.5.GA.jar
[warn] ==== oauth.net: tried
[warn]   [http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== twitter.com: tried
[warn]   [http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== atlassian: tried
[warn]   [https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== scala-tools.org: tried
[warn]   [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== public: tried
[warn]   [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn] ==== Scala-Tools Maven2 Repository: tried
[warn]   [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]   -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]   [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/kestrel/1.2.3/kestrel-1.2.3-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/kestrel/1.2.3/kestrel-1.2.3-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/apache/4/apache-4.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/mina/build/2.0.0-M6/build-2.0.0-M6.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/mina/mina-parent/2.0.0-M6/mina-parent-2.0.0-M6.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/mina/mina-core/2.0.0-M6/mina-core-2.0.0-M6-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/naggati_2.7.7/0.7.4/naggati_2.7.7-0.7.4-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/naggati_2.7.7/0.7.4/naggati_2.7.7-0.7.4-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors_2.7.7/2.0.0/twitteractors_2.7.7-2.0.0-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors_2.7.7/2.0.0/twitteractors_2.7.7-2.0.0-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors/1.1.0/twitteractors-1.1.0-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors/1.1.0/twitteractors-1.1.0-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/json/1.1.7/json-1.1.7-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/json/1.1.7/json-1.1.7-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/querulous_2.7.7/1.3.6/querulous_2.7.7-1.3.6-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/querulous_2.7.7/1.3.6/querulous_2.7.7-1.3.6-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/mysql/mysql-connector-java/5.1.13/mysql-connector-java-5.1.13-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/mysql/mysql-connector-java/5.1.13/mysql-connector-java-5.1.13-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/commons/commons-parent/12/commons-parent-12.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/results/1.0/results-1.0-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/results/1.0/results-1.0-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jmock/jmock-parent/2.4.0/jmock-parent-2.4.0.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jmock/jmock/2.4.0/jmock-2.4.0-sources.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jmock/jmock/2.4.0/jmock-2.4.0-javadoc.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-library/1.1/hamcrest-library-1.1-javadoc.jar
[info] downloading [http://maven.twttr.com/com/twitter/gizzard/1.4.10/gizzard-1.4.10.jar](http://maven.twttr.com/com/twitter/gizzard/1.4.10/gizzard-1.4.10.jar) ...
[info]     [SUCCESSFUL ] com.twitter#gizzard;1.4.10!gizzard.jar (1254ms)
[info] downloading [http://maven.twttr.com/com/twitter/results/1.0/results-1.0.jar](http://maven.twttr.com/com/twitter/results/1.0/results-1.0.jar) ...
[info]     [SUCCESSFUL ] com.twitter#results;1.0!results.jar (68ms)
[info] downloading [http://repo1.maven.org/maven2/org/slf4j/slf4j-jdk14/1.5.2/slf4j-jdk14-1.5.2.jar](http://repo1.maven.org/maven2/org/slf4j/slf4j-jdk14/1.5.2/slf4j-jdk14-1.5.2.jar) ...
[info]     [SUCCESSFUL ] org.slf4j#slf4j-jdk14;1.5.2!slf4j-jdk14.jar (89ms)
[info] downloading [http://maven.twttr.com/com/twitter/xrayspecs/1.0.7/xrayspecs-1.0.7.jar](http://maven.twttr.com/com/twitter/xrayspecs/1.0.7/xrayspecs-1.0.7.jar) ...
[info]     [SUCCESSFUL ] com.twitter#xrayspecs;1.0.7!xrayspecs.jar (47ms)
[info] downloading [http://maven.twttr.com/net/lag/configgy/1.6.8/configgy-1.6.8.jar](http://maven.twttr.com/net/lag/configgy/1.6.8/configgy-1.6.8.jar) ...
[info]     [SUCCESSFUL ] net.lag#configgy;1.6.8!configgy.jar (534ms)
[info] downloading [http://repo1.maven.org/maven2/org/slf4j/slf4j-api/1.5.2/slf4j-api-1.5.2.jar](http://repo1.maven.org/maven2/org/slf4j/slf4j-api/1.5.2/slf4j-api-1.5.2.jar) ...
[info]     [SUCCESSFUL ] org.slf4j#slf4j-api;1.5.2!slf4j-api.jar (139ms)
[info] downloading [http://maven.twttr.com/com/twitter/ostrich/1.2.7/ostrich-1.2.7.jar](http://maven.twttr.com/com/twitter/ostrich/1.2.7/ostrich-1.2.7.jar) ...
[info]     [SUCCESSFUL ] com.twitter#ostrich;1.2.7!ostrich.jar (423ms)
[info] downloading [http://maven.twttr.com/net/lag/kestrel/1.2.3/kestrel-1.2.3.jar](http://maven.twttr.com/net/lag/kestrel/1.2.3/kestrel-1.2.3.jar) ...
[info]     [SUCCESSFUL ] net.lag#kestrel;1.2.3!kestrel.jar (385ms)
[info] downloading [http://maven.twttr.com/com/twitter/json/1.1.7/json-1.1.7.jar](http://maven.twttr.com/com/twitter/json/1.1.7/json-1.1.7.jar) ...
[info]     [SUCCESSFUL ] com.twitter#json;1.1.7!json.jar (125ms)
[info] downloading [http://maven.twttr.com/thrift/libthrift/0.2.0-twitter-1/libthrift-0.2.0-twitter-1.jar](http://maven.twttr.com/thrift/libthrift/0.2.0-twitter-1/libthrift-0.2.0-twitter-1.jar) ...
[info]     [SUCCESSFUL ] thrift#libthrift;0.2.0-twitter-1!libthrift.jar (501ms)
[info] downloading [http://maven.twttr.com/com/twitter/querulous_2.7.7/1.3.6/querulous_2.7.7-1.3.6.jar](http://maven.twttr.com/com/twitter/querulous_2.7.7/1.3.6/querulous_2.7.7-1.3.6.jar) ...
[info]     [SUCCESSFUL ] com.twitter#querulous_2.7.7;1.3.6!querulous_2.7.7.jar (389ms)
[info] downloading [http://repo1.maven.org/maven2/org/scala-tools/testing/specs/1.6.2.1/specs-1.6.2.1.jar](http://repo1.maven.org/maven2/org/scala-tools/testing/specs/1.6.2.1/specs-1.6.2.1.jar) ...
[info]     [SUCCESSFUL ] org.scala-tools.testing#specs;1.6.2.1!specs.jar (5250ms)
[info] downloading [http://maven.twttr.com/org/scala-tools/vscaladoc/1.1-md-3/vscaladoc-1.1-md-3.jar](http://maven.twttr.com/org/scala-tools/vscaladoc/1.1-md-3/vscaladoc-1.1-md-3.jar) ...
[info]     [SUCCESSFUL ] org.scala-tools#vscaladoc;1.1-md-3!vscaladoc.jar (521ms)
[info] downloading [http://repo1.maven.org/maven2/asm/asm/1.5.3/asm-1.5.3.jar](http://repo1.maven.org/maven2/asm/asm/1.5.3/asm-1.5.3.jar) ...
[info]     [SUCCESSFUL ] asm#asm;1.5.3!asm.jar (132ms)
[info] downloading [http://repo1.maven.org/maven2/cglib/cglib/2.1_3/cglib-2.1_3.jar](http://repo1.maven.org/maven2/cglib/cglib/2.1_3/cglib-2.1_3.jar) ...
[info]     [SUCCESSFUL ] cglib#cglib;2.1_3!cglib.jar (1151ms)
[info] downloading [http://repo1.maven.org/maven2/org/objenesis/objenesis/1.1/objenesis-1.1.jar](http://repo1.maven.org/maven2/org/objenesis/objenesis/1.1/objenesis-1.1.jar) ...
[info]     [SUCCESSFUL ] org.objenesis#objenesis;1.1!objenesis.jar (137ms)
[info] downloading [http://repo1.maven.org/maven2/commons-logging/commons-logging/1.1/commons-logging-1.1.jar](http://repo1.maven.org/maven2/commons-logging/commons-logging/1.1/commons-logging-1.1.jar) ...
[info]     [SUCCESSFUL ] commons-logging#commons-logging;1.1!commons-logging.jar (229ms)
[info] downloading [http://repo1.maven.org/maven2/org/mockito/mockito-core/1.8.1/mockito-core-1.8.1.jar](http://repo1.maven.org/maven2/org/mockito/mockito-core/1.8.1/mockito-core-1.8.1.jar) ...
[info]     [SUCCESSFUL ] org.mockito#mockito-core;1.8.1!mockito-core.jar (3355ms)
[info] downloading [http://repo1.maven.org/maven2/org/hamcrest/hamcrest-all/1.1/hamcrest-all-1.1.jar](http://repo1.maven.org/maven2/org/hamcrest/hamcrest-all/1.1/hamcrest-all-1.1.jar) ...
[info]     [SUCCESSFUL ] org.hamcrest#hamcrest-all;1.1!hamcrest-all.jar (2241ms)
[info] downloading [http://repo1.maven.org/maven2/commons-lang/commons-lang/2.2/commons-lang-2.2.jar](http://repo1.maven.org/maven2/commons-lang/commons-lang/2.2/commons-lang-2.2.jar) ...
[info]     [SUCCESSFUL ] commons-lang#commons-lang;2.2!commons-lang.jar (423ms)
[info] downloading [http://repo1.maven.org/maven2/log4j/log4j/1.2.12/log4j-1.2.12.jar](http://repo1.maven.org/maven2/log4j/log4j/1.2.12/log4j-1.2.12.jar) ...
[info]     [SUCCESSFUL ] log4j#log4j;1.2.12!log4j.jar (672ms)
[info] downloading [http://repo1.maven.org/maven2/logkit/logkit/1.0.1/logkit-1.0.1.jar](http://repo1.maven.org/maven2/logkit/logkit/1.0.1/logkit-1.0.1.jar) ...
[info]     [SUCCESSFUL ] logkit#logkit;1.0.1!logkit.jar (196ms)
[info] downloading [http://repo1.maven.org/maven2/avalon-framework/avalon-framework/4.1.3/avalon-framework-4.1.3.jar](http://repo1.maven.org/maven2/avalon-framework/avalon-framework/4.1.3/avalon-framework-4.1.3.jar) ...
[info]     [SUCCESSFUL ] avalon-framework#avalon-framework;4.1.3!avalon-framework.jar (318ms)
[info] downloading [http://repo1.maven.org/maven2/javax/servlet/servlet-api/2.3/servlet-api-2.3.jar](http://repo1.maven.org/maven2/javax/servlet/servlet-api/2.3/servlet-api-2.3.jar) ...
[info]     [SUCCESSFUL ] javax.servlet#servlet-api;2.3!servlet-api.jar (192ms)
[info] downloading [http://repo1.maven.org/maven2/org/hamcrest/hamcrest-core/1.1/hamcrest-core-1.1.jar](http://repo1.maven.org/maven2/org/hamcrest/hamcrest-core/1.1/hamcrest-core-1.1.jar) ...
[info]     [SUCCESSFUL ] org.hamcrest#hamcrest-core;1.1!hamcrest-core.jar (513ms)
[info] downloading [http://repo1.maven.org/maven2/org/apache/mina/mina-core/2.0.0-M6/mina-core-2.0.0-M6.jar](http://repo1.maven.org/maven2/org/apache/mina/mina-core/2.0.0-M6/mina-core-2.0.0-M6.jar) ...
[info]     [SUCCESSFUL ] org.apache.mina#mina-core;2.0.0-M6!mina-core.jar(bundle) (1198ms)
[info] downloading [http://maven.twttr.com/net/lag/naggati_2.7.7/0.7.4/naggati_2.7.7-0.7.4.jar](http://maven.twttr.com/net/lag/naggati_2.7.7/0.7.4/naggati_2.7.7-0.7.4.jar) ...
[info]     [SUCCESSFUL ] net.lag#naggati_2.7.7;0.7.4!naggati_2.7.7.jar (174ms)
[info] downloading [http://maven.twttr.com/com/twitter/twitteractors/1.1.0/twitteractors-1.1.0.jar](http://maven.twttr.com/com/twitter/twitteractors/1.1.0/twitteractors-1.1.0.jar) ...
[info]     [SUCCESSFUL ] com.twitter#twitteractors;1.1.0!twitteractors.jar (369ms)
[info] downloading [http://maven.twttr.com/com/twitter/twitteractors_2.7.7/2.0.0/twitteractors_2.7.7-2.0.0.jar](http://maven.twttr.com/com/twitter/twitteractors_2.7.7/2.0.0/twitteractors_2.7.7-2.0.0.jar) ...
[info]     [SUCCESSFUL ] com.twitter#twitteractors_2.7.7;2.0.0!twitteractors_2.7.7.jar (386ms)
[info] downloading [http://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.13/mysql-connector-java-5.1.13.jar](http://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.13/mysql-connector-java-5.1.13.jar) ...
[info]     [SUCCESSFUL ] mysql#mysql-connector-java;5.1.13!mysql-connector-java.jar (1075ms)
[info] downloading [http://repo1.maven.org/maven2/commons-pool/commons-pool/1.5.4/commons-pool-1.5.4.jar](http://repo1.maven.org/maven2/commons-pool/commons-pool/1.5.4/commons-pool-1.5.4.jar) ...
[info]     [SUCCESSFUL ] commons-pool#commons-pool;1.5.4!commons-pool.jar (213ms)
[info] downloading [http://repo1.maven.org/maven2/commons-dbcp/commons-dbcp/1.4/commons-dbcp-1.4.jar](http://repo1.maven.org/maven2/commons-dbcp/commons-dbcp/1.4/commons-dbcp-1.4.jar) ...
[info]     [SUCCESSFUL ] commons-dbcp#commons-dbcp;1.4!commons-dbcp.jar (485ms)
[info] downloading [http://repo1.maven.org/maven2/org/jmock/jmock/2.4.0/jmock-2.4.0.jar](http://repo1.maven.org/maven2/org/jmock/jmock/2.4.0/jmock-2.4.0.jar) ...
[info]     [SUCCESSFUL ] org.jmock#jmock;2.4.0!jmock.jar (553ms)
[info] downloading [http://repo1.maven.org/maven2/org/hamcrest/hamcrest-library/1.1/hamcrest-library-1.1.jar](http://repo1.maven.org/maven2/org/hamcrest/hamcrest-library/1.1/hamcrest-library-1.1.jar) ...
[info]     [SUCCESSFUL ] org.hamcrest#hamcrest-library;1.1!hamcrest-library.jar (404ms)
[warn]     ::::::::::::::::::::::::::::::::::::::::::::::
[warn]     ::          UNRESOLVED DEPENDENCIES         ::
[warn]     ::::::::::::::::::::::::::::::::::::::::::::::
[warn]     :: org.jboss.netty#netty;3.1.5.GA: not found
[warn]     ::::::::::::::::::::::::::::::::::::::::::::::
[info] 
[error] :: problems summary ::
[warn] :::: WARNINGS
[warn]         module not found: org.jboss.netty#netty;3.1.5.GA
[warn]     ==== local: tried
[warn]       /root/.ivy2/local/org.jboss.netty/netty/3.1.5.GA/ivys/ivy.xml
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       /root/.ivy2/local/org.jboss.netty/netty/3.1.5.GA/jars/netty.jar
[warn]     ==== powermock-api: tried
[warn]       [http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://powermock.googlecode.com/svn/repo/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== download.java.net: tried
[warn]       [http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://download.java.net/maven/2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== localm2: tried
[warn]       /root/.ivy2/local/org/jboss/netty/netty/3.1.5.GA/ivy-3.1.5.GA.xml
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       /root/.ivy2/local/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar
[warn]     ==== testing.scala-tools.org: tried
[warn]       [http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://scala-tools.org/repo-releases/testing/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== public: tried
[warn]       [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== ibiblio: tried
[warn]       [http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://mirrors.ibiblio.org/pub/mirrors/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== local-libs: tried
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       /usr/bin/twitter-flockdb-6918136/libs/netty-3.1.5.GA.jar
[warn]     ==== oauth.net: tried
[warn]       [http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://oauth.googlecode.com/svn/code/maven/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== twitter.com: tried
[warn]       [http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://maven.twttr.com/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== atlassian: tried
[warn]       [https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== scala-tools.org: tried
[warn]       [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== public: tried
[warn]       [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://repo1.maven.org/maven2/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]     ==== Scala-Tools Maven2 Repository: tried
[warn]       [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom)
[warn]       -- artifact org.jboss.netty#netty;3.1.5.GA!netty.jar:
[warn]       [http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar](http://scala-tools.org/repo-releases/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar)
[warn]         ::::::::::::::::::::::::::::::::::::::::::::::
[warn]         ::          UNRESOLVED DEPENDENCIES         ::
[warn]         ::::::::::::::::::::::::::::::::::::::::::::::
[warn]         :: org.jboss.netty#netty;3.1.5.GA: not found
[warn]         ::::::::::::::::::::::::::::::::::::::::::::::
[error] :::: ERRORS
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/gizzard/1.4.10/gizzard-1.4.10-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/gizzard/1.4.10/gizzard-1.4.10-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/slf4j/slf4j-parent/1.5.2/slf4j-parent-1.5.2.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/slf4j/slf4j-jdk14/1.5.2/slf4j-jdk14-1.5.2-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/slf4j/slf4j-api/1.5.2/slf4j-api-1.5.2-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/configgy/1.6.8/configgy-1.6.8-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/configgy/1.6.8/configgy-1.6.8-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/ostrich/1.2.7/ostrich-1.2.7-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/ostrich/1.2.7/ostrich-1.2.7-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/scala-tools/testing/specs/1.6.2.1/specs-1.6.2.1-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/asm/asm/1.5.3/asm-1.5.3-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/asm/asm/1.5.3/asm-1.5.3-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/cglib/cglib/2.1_3/cglib-2.1_3-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/objenesis/objenesis-parent/1.1/objenesis-parent-1.1.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/commons-logging/commons-logging/1.1/commons-logging-1.1-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/log4j/log4j/1.2.12/log4j-1.2.12-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/log4j/log4j/1.2.12/log4j-1.2.12-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/logkit/logkit/1.0.1/logkit-1.0.1-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/avalon-framework/avalon-framework/4.1.3/avalon-framework-4.1.3-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/avalon-framework/avalon-framework/4.1.3/avalon-framework-4.1.3-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/javax/servlet/servlet-api/2.3/servlet-api-2.3-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/mockito/mockito-core/1.8.1/mockito-core-1.8.1-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-parent/1.1/hamcrest-parent-1.1.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-core/1.1/hamcrest-core-1.1-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-all/1.1/hamcrest-all-1.1-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.pom
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jboss/netty/netty/3.1.5.GA/netty-3.1.5.GA.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/kestrel/1.2.3/kestrel-1.2.3-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/kestrel/1.2.3/kestrel-1.2.3-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/apache/4/apache-4.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/mina/build/2.0.0-M6/build-2.0.0-M6.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/mina/mina-parent/2.0.0-M6/mina-parent-2.0.0-M6.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/mina/mina-core/2.0.0-M6/mina-core-2.0.0-M6-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/naggati_2.7.7/0.7.4/naggati_2.7.7-0.7.4-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/net/lag/naggati_2.7.7/0.7.4/naggati_2.7.7-0.7.4-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors_2.7.7/2.0.0/twitteractors_2.7.7-2.0.0-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors_2.7.7/2.0.0/twitteractors_2.7.7-2.0.0-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors/1.1.0/twitteractors-1.1.0-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/twitteractors/1.1.0/twitteractors-1.1.0-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/json/1.1.7/json-1.1.7-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/json/1.1.7/json-1.1.7-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/querulous_2.7.7/1.3.6/querulous_2.7.7-1.3.6-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/querulous_2.7.7/1.3.6/querulous_2.7.7-1.3.6-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/mysql/mysql-connector-java/5.1.13/mysql-connector-java-5.1.13-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/mysql/mysql-connector-java/5.1.13/mysql-connector-java-5.1.13-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/apache/commons/commons-parent/12/commons-parent-12.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/results/1.0/results-1.0-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/results/1.0/results-1.0-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jmock/jmock-parent/2.4.0/jmock-parent-2.4.0.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jmock/jmock/2.4.0/jmock-2.4.0-sources.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/jmock/jmock/2.4.0/jmock-2.4.0-javadoc.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/hamcrest/hamcrest-library/1.1/hamcrest-library-1.1-javadoc.jar
[info] 
[info] :: USE VERBOSE OR DEBUG MESSAGE LEVEL FOR MORE DETAILS
[error] sbt.ResolveException: unresolved dependency: org.jboss.netty#netty;3.1.5.GA: not found
[info] == update ==
[error] Error running update: sbt.ResolveException: unresolved dependency: org.jboss.netty#netty;3.1.5.GA: not found
[info] 
[info] Total time: 1327 s, completed Nov 8, 2010 10:28:38 AM
[info] 
[info] Total session time: 1362 s, completed Nov 8, 2010 10:28:38 AM
[error] Error during build.
[/SIZE]

---

