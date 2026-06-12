---
title: "Java MySQL Connect problem"
date: 2011-04-29
forum: General Help
---

### Post by Fochest on 2011-04-29
Hello everybody,

I upgraded from 10.10 to 11.04 and since then I am not able to build my java projects that worked fine under 10.10. (and still does under other 10.10s)

Quick overview about my setup:

java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode

mvn -v
Apache Maven 2.2.1 (rdebian-4)
Java version: 1.6.0_24
Java home: /usr/lib/jvm/java-6-sun-1.6.0.24/jre
Default locale: de_DE, platform encoding: UTF-8
OS name: "linux" version: "2.6.38-8-generic" arch: "amd64" Family: "unix"

package libmysql-java - Java database (JDBC) driver for MySQL
installed

So. In my multi-maven project I am trying to open a connection to a remote mysql database which is accessible: console mysql command works so no firewall. But when I am trying to open the connection in java (in a jUnit test) the build-process gets stuck. 

jstack prints out this (for one of the threads):
main" prio=10 tid=0x000000004116a000 nid=0x6f8a runnable [0x00007f038fc48000]
   java.lang.Thread.State: RUNNABLE
        at java.net.PlainSocketImpl.socketAvailable(Native Method)
        at java.net.PlainSocketImpl.available(PlainSocketImpl.java:472)
        - locked <0x0000000783d64dc8> (a java.net.SocksSocketImpl)
        at java.net.SocketInputStream.available(SocketInputStream.java:217)
        at java.io.BufferedInputStream.available(BufferedInputStream.java:381)
        - locked <0x0000000783d651c8> (a java.io.BufferedInputStream)
        at com.mysql.jdbc.MysqlIO.clearInputStream(MysqlIO.java:2073)
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:1898)
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:1831)
        at com.mysql.jdbc.MysqlIO.secureAuth411(MysqlIO.java:2389)
        at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:757)
        at com.mysql.jdbc.Connection.createNewIO(Connection.java:1654)
        at com.mysql.jdbc.Connection.<init>(Connection.java:432)
        at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:400)
        at org.apache.commons.dbcp.DriverConnectionFactory.createConnection(DriverConnectionFactory.java:38)

First I thought about apparmor which has been shut down but nevertheless still no connection is available.

Am I overseeing something?

Thanks in advance.
Regards,
Fochest

---

### Post by Fochest on 2011-05-05
btw the process that runs the tests is at 100% process load

3153 pts/0    Sl+   26:16 /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java -jar /tmp/surefirebooter4019024954282259786.jar /tmp/surefire1719942936188918104tmp /tmp/surefire2487801693506367876tmp

3153 user     20   0 2295m 151m  11m S  102  1.9  28:07.44 java

Noone any ideas?

Regards,
Fochest

---

### Post by Fochest on 2011-05-10
Somehow it did not work on several natty computers. 

Found a solution:

Upgraded the mysql-connector-java jar to 5.1.16 and now the connection is established.

---

