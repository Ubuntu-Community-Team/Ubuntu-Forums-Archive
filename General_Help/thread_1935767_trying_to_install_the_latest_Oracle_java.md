---
title: "trying to install the latest Oracle java"
date: 2012-03-05
forum: General Help
---

### Post by bjlockie on 2012-03-05
I am trying to install the latest Oracle java.

I created /usr/local/java and put jre1.7.0_03 in that directory.

I linked latest to /usr/local/java/jre1.7.0_03/

ll /usr/local/java
total 33076
drwxr-xr-x  3 root root     4096 2012-03-04 23:23 ./
drwxr-xr-x 11 root root     4096 2012-03-04 22:29 ../
drwxr-xr-x  6 uucp  143     4096 2012-03-04 22:25 jre1.7.0_03/
-rw-rw-r--  1 rjl  rjl  33853947 2012-01-23 15:35 jre-7u3-linux-i586.tar.gz
lrwxrwxrwx  1 root root       27 2012-03-04 23:23 latest -> /usr/local/java/jre1.7.0_03/

I edited /etc/environment to have:
JAVA_HOME="/usr/local/java/latest"
JRE_HOME="/usr/local/java/latest"
PATH="/usr/local/java/latest/bin:\
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

$ java -version shows:
java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) Client VM (build 22.1-b02, mixed mode)


I use firefox so I created a link for the java plugin and changed the about:config
java.default_java_location_others;/usr/local/java/latest
java.java_plugin_library_name;libjavaplugin_oji

ll /usr/lib/mozilla/plugins/libjavaplugin_oji.so 
lrwxrwxrwx 1 root root 59 2012-03-04 23:50 /usr/lib/mozilla/plugins/libjavaplugin_oji.so -> /usr/local/java/latest/plugin/i386/ns7/libjavaplugin_oji.so

The tests say I don't have java.

---

### Post by lovinglinux on 2012-03-05
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

