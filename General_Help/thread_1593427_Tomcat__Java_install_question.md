---
title: "Tomcat / Java install question"
date: 2010-10-11
forum: General Help
---

### Post by bscenefilms on 2010-10-11
I have installed the JVM etc. and when I look in usr/lib I see:

jvm:
total 84
drwxr-xr-x   3 root root  4096 2010-09-27 13:30 .
drwxr-xr-x 210 root root 69632 2010-10-11 09:01 ..
lrwxrwxrwx   1 root root    14 2010-09-27 13:30 default-java -> java-6-openjdk
lrwxrwxrwx   1 root root    14 2010-09-27 13:30 java-1.6.0-openjdk -> java-6-openjdk
drwxr-xr-x   5 root root  4096 2010-09-27 13:30 java-6-openjdk
-rw-r--r--   1 root root  2313 2010-07-27 01:42 .java-6-openjdk.jinfo

Looking at the Tomcat install instructions here:

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

What do I set the JAVA_HOME var to for this?  It was not set by the installer...

Moreover, I also have Tomcat installed and I know it's there because I see it getting shut down when I restart but I have no idea where it is at - or if it needs the JAVA_HOME to be set since clearly, it IS running.  I want to setup a Shibboleth iDP and I think it will want to see the $TOMCAT vars and those do not appear to be set either...

Can anyone shed light here?

TIA!

---

### Post by bscenefilms on 2010-10-11
Nobody?

---

### Post by freedomAboveAll on 2010-10-11
> **bscenefilms said:**
> I have installed the JVM etc. and when I look in usr/lib I see:

jvm:
total 84
drwxr-xr-x   3 root root  4096 2010-09-27 13:30 .
drwxr-xr-x 210 root root 69632 2010-10-11 09:01 ..
lrwxrwxrwx   1 root root    14 2010-09-27 13:30 default-java -> java-6-openjdk
lrwxrwxrwx   1 root root    14 2010-09-27 13:30 java-1.6.0-openjdk -> java-6-openjdk
drwxr-xr-x   5 root root  4096 2010-09-27 13:30 java-6-openjdk
-rw-r--r--   1 root root  2313 2010-07-27 01:42 .java-6-openjdk.jinfo

Looking at the Tomcat install instructions here:

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

What do I set the JAVA_HOME var to for this?  It was not set by the installer...

Moreover, I also have Tomcat installed and I know it's there because I see it getting shut down when I restart but I have no idea where it is at - or if it needs the JAVA_HOME to be set since clearly, it IS running.  I want to setup a Shibboleth iDP and I think it will want to see the $TOMCAT vars and those do not appear to be set either...

Can anyone shed light here?

TIA!

Hi -

First, I would try tomcat6 in the repositories myself; that article appears old and Synaptic has Tomcat6.

To locate your installation try :

> locate tomcat

If tomcat is running, like you say, your JAVA_HOME may be set.



Hope this helps for starters ...

---

### Post by bscenefilms on 2010-10-11
When I echo $JAVA_HOME I get nothing...

When I do a locate tomcat I get this:

/etc/tomcat6
/etc/cron.daily/tomcat6
/etc/default/tomcat6
/etc/init.d/tomcat6
/etc/rc0.d/K08tomcat6
/etc/rc1.d/K08tomcat6
/etc/rc2.d/S92tomcat6
/etc/rc3.d/S92tomcat6
/etc/rc4.d/S92tomcat6
/etc/rc5.d/S92tomcat6
/etc/rc6.d/K08tomcat6
/etc/tomcat6/Catalina
/etc/tomcat6/catalina.properties
/etc/tomcat6/context.xml
/etc/tomcat6/logging.properties
/etc/tomcat6/policy.d
/etc/tomcat6/server.xml
/etc/tomcat6/tomcat-users.xml
/etc/tomcat6/web.xml
/etc/tomcat6/Catalina/localhost
/etc/tomcat6/Catalina/localhost/ROOT.xml
/etc/tomcat6/policy.d/01system.policy
/etc/tomcat6/policy.d/02debian.policy
/etc/tomcat6/policy.d/03catalina.policy
/etc/tomcat6/policy.d/04webapps.policy
/etc/tomcat6/policy.d/50local.policy
/home/mflynn/Downloads/apache-tomcat-6.0.29.tar.gz
/usr/local/Tomcat/bin/tomcat-juli.jar
/usr/local/Tomcat/bin/tomcat-native.tar.gz
/usr/local/Tomcat/conf/tomcat-users.xml
/usr/local/Tomcat/lib/tomcat-coyote.jar
/usr/local/Tomcat/lib/tomcat-dbcp.jar
/usr/local/Tomcat/lib/tomcat-i18n-es.jar
/usr/local/Tomcat/lib/tomcat-i18n-fr.jar
/usr/local/Tomcat/lib/tomcat-i18n-ja.jar
/usr/local/Tomcat/webapps/ROOT/tomcat-power.gif
/usr/local/Tomcat/webapps/ROOT/tomcat.gif
/usr/local/Tomcat/webapps/ROOT/tomcat.svg
/usr/local/Tomcat/webapps/docs/appdev/sample/web/images/tomcat.gif
/usr/local/Tomcat/webapps/docs/images/tomcat.gif
/usr/local/Tomcat/webapps/docs/images/tomcat.svg
/usr/local/Tomcat/webapps/host-manager/images/tomcat.gif
/usr/local/Tomcat/webapps/manager/images/tomcat.gif
/usr/share/tomcat6
/usr/share/doc/libtomcat6-java
/usr/share/doc/tomcat6
/usr/share/doc/tomcat6-common
/usr/share/doc/libtomcat6-java/changelog.Debian.gz
/usr/share/doc/libtomcat6-java/copyright
/usr/share/doc/tomcat6/README.Debian.gz
/usr/share/doc/tomcat6/changelog.Debian.gz
/usr/share/doc/tomcat6/copyright
/usr/share/doc/tomcat6-common/README.Debian.gz
/usr/share/doc/tomcat6-common/RELEASE-NOTES.gz
/usr/share/doc/tomcat6-common/RUNNING.txt.gz
/usr/share/doc/tomcat6-common/changelog.Debian.gz
/usr/share/doc/tomcat6-common/copyright
/usr/share/java/tomcat-coyote-6.0.24.jar
/usr/share/java/tomcat-coyote.jar
/usr/share/java/tomcat-i18n-es-6.0.24.jar
/usr/share/java/tomcat-i18n-es.jar
/usr/share/java/tomcat-i18n-fr-6.0.24.jar
/usr/share/java/tomcat-i18n-fr.jar
/usr/share/java/tomcat-i18n-ja-6.0.24.jar
/usr/share/java/tomcat-i18n-ja.jar
/usr/share/java/tomcat-juli-6.0.24.jar
/usr/share/java/tomcat-juli.jar
/usr/share/maven-repo/org/apache/tomcat
/usr/share/maven-repo/org/apache/tomcat/annotations-api
/usr/share/maven-repo/org/apache/tomcat/catalina
/usr/share/maven-repo/org/apache/tomcat/catalina-ha
/usr/share/maven-repo/org/apache/tomcat/coyote
/usr/share/maven-repo/org/apache/tomcat/jasper
/usr/share/maven-repo/org/apache/tomcat/jasper-el
/usr/share/maven-repo/org/apache/tomcat/juli
/usr/share/maven-repo/org/apache/tomcat/tribes
/usr/share/maven-repo/org/apache/tomcat/annotations-api/6.0.24
/usr/share/maven-repo/org/apache/tomcat/annotations-api/debian
/usr/share/maven-repo/org/apache/tomcat/annotations-api/6.0.24/annotations-api-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/annotations-api/6.0.24/annotations-api-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/annotations-api/debian/annotations-api-debian.jar
/usr/share/maven-repo/org/apache/tomcat/annotations-api/debian/annotations-api-debian.pom
/usr/share/maven-repo/org/apache/tomcat/catalina/6.0.24
/usr/share/maven-repo/org/apache/tomcat/catalina/debian
/usr/share/maven-repo/org/apache/tomcat/catalina/6.0.24/catalina-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/catalina/6.0.24/catalina-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/catalina/debian/catalina-debian.jar
/usr/share/maven-repo/org/apache/tomcat/catalina/debian/catalina-debian.pom
/usr/share/maven-repo/org/apache/tomcat/catalina-ha/6.0.24
/usr/share/maven-repo/org/apache/tomcat/catalina-ha/debian
/usr/share/maven-repo/org/apache/tomcat/catalina-ha/6.0.24/catalina-ha-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/catalina-ha/6.0.24/catalina-ha-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/catalina-ha/debian/catalina-ha-debian.jar
/usr/share/maven-repo/org/apache/tomcat/catalina-ha/debian/catalina-ha-debian.pom
/usr/share/maven-repo/org/apache/tomcat/coyote/6.0.24
/usr/share/maven-repo/org/apache/tomcat/coyote/debian
/usr/share/maven-repo/org/apache/tomcat/coyote/6.0.24/coyote-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/coyote/6.0.24/coyote-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/coyote/debian/coyote-debian.jar
/usr/share/maven-repo/org/apache/tomcat/coyote/debian/coyote-debian.pom
/usr/share/maven-repo/org/apache/tomcat/jasper/6.0.24
/usr/share/maven-repo/org/apache/tomcat/jasper/debian
/usr/share/maven-repo/org/apache/tomcat/jasper/6.0.24/jasper-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/jasper/6.0.24/jasper-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/jasper/debian/jasper-debian.jar
/usr/share/maven-repo/org/apache/tomcat/jasper/debian/jasper-debian.pom
/usr/share/maven-repo/org/apache/tomcat/jasper-el/6.0.24
/usr/share/maven-repo/org/apache/tomcat/jasper-el/debian
/usr/share/maven-repo/org/apache/tomcat/jasper-el/6.0.24/jasper-el-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/jasper-el/6.0.24/jasper-el-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/jasper-el/debian/jasper-el-debian.jar
/usr/share/maven-repo/org/apache/tomcat/jasper-el/debian/jasper-el-debian.pom
/usr/share/maven-repo/org/apache/tomcat/juli/6.0.24
/usr/share/maven-repo/org/apache/tomcat/juli/debian
/usr/share/maven-repo/org/apache/tomcat/juli/6.0.24/juli-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/juli/6.0.24/juli-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/juli/debian/juli-debian.jar
/usr/share/maven-repo/org/apache/tomcat/juli/debian/juli-debian.pom
/usr/share/maven-repo/org/apache/tomcat/tribes/6.0.24
/usr/share/maven-repo/org/apache/tomcat/tribes/debian
/usr/share/maven-repo/org/apache/tomcat/tribes/6.0.24/tribes-6.0.24.jar
/usr/share/maven-repo/org/apache/tomcat/tribes/6.0.24/tribes-6.0.24.pom
/usr/share/maven-repo/org/apache/tomcat/tribes/debian/tribes-debian.jar
/usr/share/maven-repo/org/apache/tomcat/tribes/debian/tribes-debian.pom
/usr/share/tomcat6/bin
/usr/share/tomcat6/lib
/usr/share/tomcat6/webapps
/usr/share/tomcat6/bin/bootstrap.jar
/usr/share/tomcat6/bin/catalina-tasks.xml
/usr/share/tomcat6/bin/catalina.sh
/usr/share/tomcat6/bin/digest.sh
/usr/share/tomcat6/bin/setclasspath.sh
/usr/share/tomcat6/bin/shutdown.sh
/usr/share/tomcat6/bin/startup.sh
/usr/share/tomcat6/bin/tomcat-juli.jar
/usr/share/tomcat6/bin/tool-wrapper.sh
/usr/share/tomcat6/bin/version.sh
/usr/share/tomcat6/lib/annotations-api.jar
/usr/share/tomcat6/lib/catalina-ant.jar
/usr/share/tomcat6/lib/catalina-ha.jar
/usr/share/tomcat6/lib/catalina-tribes.jar
/usr/share/tomcat6/lib/catalina.jar
/usr/share/tomcat6/lib/commons-dbcp.jar
/usr/share/tomcat6/lib/commons-pool.jar
/usr/share/tomcat6/lib/el-api.jar
/usr/share/tomcat6/lib/jasper-el.jar
/usr/share/tomcat6/lib/jasper-jdt.jar
/usr/share/tomcat6/lib/jasper.jar
/usr/share/tomcat6/lib/jsp-api.jar
/usr/share/tomcat6/lib/servlet-api.jar
/usr/share/tomcat6/lib/tomcat-coyote.jar
/usr/share/tomcat6/lib/tomcat-i18n-es.jar
/usr/share/tomcat6/lib/tomcat-i18n-fr.jar
/usr/share/tomcat6/lib/tomcat-i18n-ja.jar
/usr/share/tomcat6/webapps/default_root
/usr/share/tomcat6/webapps/default_root/META-INF
/usr/share/tomcat6/webapps/default_root/index.html
/usr/share/tomcat6/webapps/default_root/META-INF/context.xml
/usr/share/ubuntu-serverguide/html/C/tomcat.html
/var/cache/tomcat6
/var/cache/apt/archives/libtomcat6-java_6.0.24-2ubuntu1.3_all.deb
/var/cache/apt/archives/tomcat6-common_6.0.24-2ubuntu1.3_all.deb
/var/cache/apt/archives/tomcat6_6.0.24-2ubuntu1.3_all.deb
/var/cache/tomcat6/Catalina
/var/cache/tomcat6/catalina.policy
/var/cache/tomcat6/Catalina/localhost
/var/cache/tomcat6/Catalina/localhost/_
/var/lib/tomcat6
/var/lib/dpkg/info/libtomcat6-java.list
/var/lib/dpkg/info/libtomcat6-java.md5sums
/var/lib/dpkg/info/tomcat6-common.list
/var/lib/dpkg/info/tomcat6-common.md5sums
/var/lib/dpkg/info/tomcat6.conffiles
/var/lib/dpkg/info/tomcat6.list
/var/lib/dpkg/info/tomcat6.md5sums
/var/lib/dpkg/info/tomcat6.postinst
/var/lib/dpkg/info/tomcat6.postrm
/var/lib/dpkg/info/tomcat6.prerm
/var/lib/tomcat6/common
/var/lib/tomcat6/conf
/var/lib/tomcat6/logs
/var/lib/tomcat6/server
/var/lib/tomcat6/shared
/var/lib/tomcat6/webapps
/var/lib/tomcat6/work
/var/lib/tomcat6/common/classes
/var/lib/tomcat6/server/classes
/var/lib/tomcat6/shared/classes
/var/lib/tomcat6/webapps/ROOT
/var/lib/tomcat6/webapps/ROOT/META-INF
/var/lib/tomcat6/webapps/ROOT/index.html
/var/lib/tomcat6/webapps/ROOT/META-INF/context.xml
/var/lib/update-rc.d/tomcat6
/var/log/tomcat6
/var/log/tomcat6/catalina.2010-09-27.log
/var/log/tomcat6/catalina.2010-10-11.log
/var/log/tomcat6/catalina.out
/var/log/tomcat6/localhost.2010-09-27.log
/var/log/tomcat6/localhost.2010-10-11.log

So it looks like it's there - How can I test it to see if I even need to set that var?

---

### Post by bscenefilms on 2010-10-12
Anyone?

---

### Post by lykeion on 2010-10-12
I think tomcat uses the JAVA_HOME variable in file /etc/default/tomcat6.
You could test if it's running ok by enter [http://localhost:8080](http://localhost:8080) in a browser.
Read more here: [https://help.ubuntu.com/10.04/serverguide/C/tomcat.html](https://help.ubuntu.com/10.04/serverguide/C/tomcat.html)

---

### Post by bscenefilms on 2010-10-12
Well Tomcat works heh.

---

