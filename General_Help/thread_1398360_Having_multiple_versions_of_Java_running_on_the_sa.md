---
title: "Having multiple versions of Java running on the same computer"
date: 2010-02-04
forum: General Help
---

### Post by EricDallal on 2010-02-04
Hello,

I am a graduate student who is having problems with software that I need for a course (as well as for my own project). The main problem is that the software was developed about 15 years ago and is incompatible with the most current version of Java. I would like to know how to install an older version of Java so that I can use it with just this one application, without changing the version of Java that I use for everything else.

Any help would be appreciated. Please ask if you need more information.

Thanks,

Eric

---

### Post by doas777 on 2010-02-04
well, as I understand it (an my understanding is far from complete), you can install multiple versions of java on your system. the problem comes in when an app determines what runtime to use. you can find older jres in synaptic or download them from sun.

by default the jre used defaults to whatever is set in teh "alternatives". the alternative is just a link from /usr/bin/java to whatever specific jre is to be used by defaults.

I ran these commands to track my jre back to the alternatives (ll is an alias for ls -l):
```
**karmic:~$ which java**
/usr/bin/java
**karmic:~$ ll /usr/bin | grep java**
-rwxr-xr-x 1 root   root       2506 2009-08-25 09:24 dh_nativejava
lrwxrwxrwx 1 root   root         22 2009-11-05 10:53 java -> /etc/alternatives/java
lrwxrwxrwx 1 root   root         23 2009-11-05 10:53 javac -> /etc/alternatives/javac
lrwxrwxrwx 1 root   root         25 2009-11-05 10:53 javadoc -> /etc/alternatives/javadoc
lrwxrwxrwx 1 root   root         23 2009-11-05 10:53 javah -> /etc/alternatives/javah
lrwxrwxrwx 1 root   root         23 2009-11-05 10:53 javap -> /etc/alternatives/javap
lrwxrwxrwx 1 root   root         24 2009-11-05 10:53 javaws -> /etc/alternatives/javaws
**karmic:~$ ll /etc/alternatives/ | grep java**
lrwxrwxrwx 1 root root  44 2009-11-05 10:53 appletviewer -> /usr/lib/jvm/java-6-openjdk/bin/appletviewer
lrwxrwxrwx 1 root root  54 2009-11-05 10:53 appletviewer.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/appletviewer.1.gz
lrwxrwxrwx 1 root root  35 2009-11-05 10:53 apt -> /usr/lib/jvm/java-6-openjdk/bin/apt
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 apt.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/apt.1.gz
lrwxrwxrwx 1 root root  40 2009-11-05 10:53 extcheck -> /usr/lib/jvm/java-6-openjdk/bin/extcheck
lrwxrwxrwx 1 root root  50 2009-11-05 10:53 extcheck.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/extcheck.1.gz
lrwxrwxrwx 1 root root  36 2009-11-05 10:53 idlj -> /usr/lib/jvm/java-6-openjdk/bin/idlj
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 idlj.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/idlj.1.gz
lrwxrwxrwx 1 root root  35 2009-11-05 10:53 jar -> /usr/lib/jvm/java-6-openjdk/bin/jar
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 jar.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jar.1.gz
lrwxrwxrwx 1 root root  41 2009-11-05 10:53 jarsigner -> /usr/lib/jvm/java-6-openjdk/bin/jarsigner
lrwxrwxrwx 1 root root  51 2009-11-05 10:53 jarsigner.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jarsigner.1.gz
lrwxrwxrwx 1 root root  40 2009-11-05 10:53 java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java
lrwxrwxrwx 1 root root  50 2009-11-05 10:53 java.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
lrwxrwxrwx 1 root root  37 2009-11-05 10:53 javac -> /usr/lib/jvm/java-6-openjdk/bin/javac
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 javac.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/javac.1.gz
lrwxrwxrwx 1 root root  39 2009-11-05 10:53 javadoc -> /usr/lib/jvm/java-6-openjdk/bin/javadoc
lrwxrwxrwx 1 root root  49 2009-11-05 10:53 javadoc.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/javadoc.1.gz
lrwxrwxrwx 1 root root  37 2009-11-05 10:53 javah -> /usr/lib/jvm/java-6-openjdk/bin/javah
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 javah.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/javah.1.gz
lrwxrwxrwx 1 root root  37 2009-11-05 10:53 javap -> /usr/lib/jvm/java-6-openjdk/bin/javap
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 javap.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/javap.1.gz
lrwxrwxrwx 1 root root  42 2009-11-05 10:53 javaws -> /usr/lib/jvm/java-6-openjdk/jre/bin/javaws
lrwxrwxrwx 1 root root  52 2009-11-05 10:53 javaws.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/javaws.1.gz
lrwxrwxrwx 1 root root  40 2009-11-05 10:53 jconsole -> /usr/lib/jvm/java-6-openjdk/bin/jconsole
lrwxrwxrwx 1 root root  50 2009-11-05 10:53 jconsole.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jconsole.1.gz
lrwxrwxrwx 1 root root  35 2009-11-05 10:53 jdb -> /usr/lib/jvm/java-6-openjdk/bin/jdb
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 jdb.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jdb.1.gz
lrwxrwxrwx 1 root root  41 2009-11-05 10:53 jexec -> /usr/lib/jvm/java-6-openjdk/jre/lib/jexec
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 jexec-binfmt -> /usr/lib/jvm/java-6-openjdk/jre/lib/jar.binfmt
lrwxrwxrwx 1 root root  36 2009-11-05 10:53 jhat -> /usr/lib/jvm/java-6-openjdk/bin/jhat
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 jhat.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jhat.1.gz
lrwxrwxrwx 1 root root  37 2009-11-05 10:53 jinfo -> /usr/lib/jvm/java-6-openjdk/bin/jinfo
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 jinfo.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jinfo.1.gz
lrwxrwxrwx 1 root root  36 2009-11-05 10:53 jmap -> /usr/lib/jvm/java-6-openjdk/bin/jmap
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 jmap.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jmap.1.gz
lrwxrwxrwx 1 root root  35 2009-11-05 10:53 jps -> /usr/lib/jvm/java-6-openjdk/bin/jps
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 jps.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jps.1.gz
lrwxrwxrwx 1 root root  42 2009-11-05 10:53 jrunscript -> /usr/lib/jvm/java-6-openjdk/bin/jrunscript
lrwxrwxrwx 1 root root  52 2009-11-05 10:53 jrunscript.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jrunscript.1.gz
lrwxrwxrwx 1 root root  41 2009-11-05 10:53 jsadebugd -> /usr/lib/jvm/java-6-openjdk/bin/jsadebugd
lrwxrwxrwx 1 root root  51 2009-11-05 10:53 jsadebugd.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jsadebugd.1.gz
lrwxrwxrwx 1 root root  38 2009-11-05 10:53 jstack -> /usr/lib/jvm/java-6-openjdk/bin/jstack
lrwxrwxrwx 1 root root  48 2009-11-05 10:53 jstack.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jstack.1.gz
lrwxrwxrwx 1 root root  37 2009-11-05 10:53 jstat -> /usr/lib/jvm/java-6-openjdk/bin/jstat
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 jstat.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jstat.1.gz
lrwxrwxrwx 1 root root  38 2009-11-05 10:53 jstatd -> /usr/lib/jvm/java-6-openjdk/bin/jstatd
lrwxrwxrwx 1 root root  48 2009-11-05 10:53 jstatd.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/jstatd.1.gz
lrwxrwxrwx 1 root root  43 2009-11-05 10:53 keytool -> /usr/lib/jvm/java-6-openjdk/jre/bin/keytool
lrwxrwxrwx 1 root root  53 2009-11-05 10:53 keytool.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/keytool.1.gz
lrwxrwxrwx 1 root root  44 2009-11-05 10:53 native2ascii -> /usr/lib/jvm/java-6-openjdk/bin/native2ascii
lrwxrwxrwx 1 root root  54 2009-11-05 10:53 native2ascii.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/native2ascii.1.gz
lrwxrwxrwx 1 root root  40 2009-11-05 10:53 orbd -> /usr/lib/jvm/java-6-openjdk/jre/bin/orbd
lrwxrwxrwx 1 root root  50 2009-11-05 10:53 orbd.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/orbd.1.gz
lrwxrwxrwx 1 root root  43 2009-11-05 10:53 pack200 -> /usr/lib/jvm/java-6-openjdk/jre/bin/pack200
lrwxrwxrwx 1 root root  53 2009-11-05 10:53 pack200.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/pack200.1.gz
lrwxrwxrwx 1 root root  54 2009-11-05 10:53 pluginappletviewer -> /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 policytool -> /usr/lib/jvm/java-6-openjdk/jre/bin/policytool
lrwxrwxrwx 1 root root  56 2009-11-05 10:53 policytool.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/policytool.1.gz
lrwxrwxrwx 1 root root  36 2009-11-05 10:53 rmic -> /usr/lib/jvm/java-6-openjdk/bin/rmic
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 rmic.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/rmic.1.gz
lrwxrwxrwx 1 root root  40 2009-11-05 10:53 rmid -> /usr/lib/jvm/java-6-openjdk/jre/bin/rmid
lrwxrwxrwx 1 root root  50 2009-11-05 10:53 rmid.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/rmid.1.gz
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 rmiregistry -> /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry
lrwxrwxrwx 1 root root  57 2009-11-05 10:53 rmiregistry.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/rmiregistry.1.gz
lrwxrwxrwx 1 root root  41 2009-11-05 10:53 schemagen -> /usr/lib/jvm/java-6-openjdk/bin/schemagen
lrwxrwxrwx 1 root root  51 2009-11-05 10:53 schemagen.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/schemagen.1.gz
lrwxrwxrwx 1 root root  41 2009-11-05 10:53 serialver -> /usr/lib/jvm/java-6-openjdk/bin/serialver
lrwxrwxrwx 1 root root  51 2009-11-05 10:53 serialver.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/serialver.1.gz
lrwxrwxrwx 1 root root  46 2009-11-05 10:53 servertool -> /usr/lib/jvm/java-6-openjdk/jre/bin/servertool
lrwxrwxrwx 1 root root  56 2009-11-05 10:53 servertool.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/servertool.1.gz
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 tnameserv -> /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv
lrwxrwxrwx 1 root root  55 2009-11-05 10:53 tnameserv.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/tnameserv.1.gz
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 unpack200 -> /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200
lrwxrwxrwx 1 root root  55 2009-11-05 10:53 unpack200.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/unpack200.1.gz
lrwxrwxrwx 1 root root  37 2009-11-05 10:53 wsgen -> /usr/lib/jvm/java-6-openjdk/bin/wsgen
lrwxrwxrwx 1 root root  47 2009-11-05 10:53 wsgen.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/wsgen.1.gz
lrwxrwxrwx 1 root root  40 2009-11-05 10:53 wsimport -> /usr/lib/jvm/java-6-openjdk/bin/wsimport
lrwxrwxrwx 1 root root  50 2009-11-05 10:53 wsimport.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/wsimport.1.gz
lrwxrwxrwx 1 root root  35 2009-11-05 10:53 xjc -> /usr/lib/jvm/java-6-openjdk/bin/xjc
lrwxrwxrwx 1 root root  45 2009-11-05 10:53 xjc.1.gz -> /usr/lib/jvm/java-6-openjdk/man/man1/xjc.1.gz
karmic:~$ 


```so I can see that my jre is located at /usr/lib/jvm/java-6-openjdk

to run an app against an older framework, just specify the full path of the jre
eg: ```
/usr/lib/jvm/java-6-openjdk/bin/java -jar <path to jarfile>
```hth

---

