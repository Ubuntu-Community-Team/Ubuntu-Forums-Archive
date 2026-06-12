---
title: "Java : Sun JDK or OpenJDK ??"
date: 2011-03-16
forum: General Help
---

### Post by ShaneQful on 2011-03-16
Hey I installed the java jdk and jre from the software center & I was wondering when I use eclipse or the command line am I using the open jdk or the sun java jdk. I need to have the sun jdk running for a college project.

---

### Post by lykeion on 2011-03-16
_Command-line_
List all installed java versions with:
```
update-java-alternatives --list
```
And set version with (<jname> is the short name, ex java-6-sun for Sun Java):
```
update-java-alternatives --set <jname>
```
Check currently used JDK:
```
javac -version
```
javac 1.6.0_24 --> Sun Java JDK
javac 1.6.0_18b (or similar, not sure since I don't have it installed myself) --> OpenJDK JDK

_Eclipse_
To add/edit Java JREs:
Window > Preferences > Java > Installed JREs

EDIT
You don't need both JDK and JRE (since the former include the latter).
So if you want to run *and* develop Java you just need the JDK and can uninstall the JRE.

---

### Post by Paddy Landau on 2011-03-17
@lykeion: Thank you for posting those. I presume I have Sun's version installed, because:
```
*update-java-alternatives --list*
java-6-sun 63 /usr/lib/jvm/java-6-sun
```However, when I try to run *javac*, I'm told it is not installed:
```
*javac -version*
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>
```Is that because I am interested only in JRE and not JDK? Or is something else going on?

---

### Post by lykeion on 2011-03-17
Yes it seems that you have Sun Java installed, but the --list switch won't tell you if it's only JRE or the whole JDK. Read manual entry about update-java-alternatives to see how to use the --verbose switch:
```
man update-java-alternatives
```
From your javac output it seems that it's the Sun Java JRE you have, since javac (java compiler) is part of JDK.

I'm not sure if you (like OP) *want* to install JDK, or just want some clarifications about jdk/jre/javac?
If you *do* want to install Sun Java JDK I'd suggest you to uninstall Sun Java JRE and install the JDK.

---

### Post by Paddy Landau on 2011-03-17
Thanks for the answers. I'm not a developer, so the JRE will suffice for me.

Here are my results:
```
*update-java-alternatives --verbose --list*
listing java alternatives:
java-6-sun 63 /usr/lib/jvm/java-6-sun
jre ControlPanel /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel
jre java /usr/lib/jvm/java-6-sun/jre/bin/java
jre java_vm /usr/lib/jvm/java-6-sun/jre/bin/java_vm
jre javaws /usr/lib/jvm/java-6-sun/jre/bin/javaws
jre jcontrol /usr/lib/jvm/java-6-sun/jre/bin/jcontrol
jre keytool /usr/lib/jvm/java-6-sun/jre/bin/keytool
jre pack200 /usr/lib/jvm/java-6-sun/jre/bin/pack200
jre policytool /usr/lib/jvm/java-6-sun/jre/bin/policytool
jre rmid /usr/lib/jvm/java-6-sun/jre/bin/rmid
jre rmiregistry /usr/lib/jvm/java-6-sun/jre/bin/rmiregistry
jre unpack200 /usr/lib/jvm/java-6-sun/jre/bin/unpack200
jre orbd /usr/lib/jvm/java-6-sun/jre/bin/orbd
jre servertool /usr/lib/jvm/java-6-sun/jre/bin/servertool
jre tnameserv /usr/lib/jvm/java-6-sun/jre/bin/tnameserv
jre jexec /usr/lib/jvm/java-6-sun/jre/lib/jexec
jdk HtmlConverter /usr/lib/jvm/java-6-sun/bin/HtmlConverter
jdk appletviewer /usr/lib/jvm/java-6-sun/bin/appletviewer
jdk apt /usr/lib/jvm/java-6-sun/bin/apt
jdk extcheck /usr/lib/jvm/java-6-sun/bin/extcheck
jdk idlj /usr/lib/jvm/java-6-sun/bin/idlj
jdk jar /usr/lib/jvm/java-6-sun/bin/jar
jdk jarsigner /usr/lib/jvm/java-6-sun/bin/jarsigner
jdk javac /usr/lib/jvm/java-6-sun/bin/javac
jdk javadoc /usr/lib/jvm/java-6-sun/bin/javadoc
jdk javah /usr/lib/jvm/java-6-sun/bin/javah
jdk javap /usr/lib/jvm/java-6-sun/bin/javap
jdk jconsole /usr/lib/jvm/java-6-sun/bin/jconsole
jdk jdb /usr/lib/jvm/java-6-sun/bin/jdb
jdk jhat /usr/lib/jvm/java-6-sun/bin/jhat
jdk jinfo /usr/lib/jvm/java-6-sun/bin/jinfo
jdk jmap /usr/lib/jvm/java-6-sun/bin/jmap
jdk jps /usr/lib/jvm/java-6-sun/bin/jps
jdk jrunscript /usr/lib/jvm/java-6-sun/bin/jrunscript
jdk jsadebugd /usr/lib/jvm/java-6-sun/bin/jsadebugd
jdk jstack /usr/lib/jvm/java-6-sun/bin/jstack
jdk jstat /usr/lib/jvm/java-6-sun/bin/jstat
jdk jstatd /usr/lib/jvm/java-6-sun/bin/jstatd
jdk native2ascii /usr/lib/jvm/java-6-sun/bin/native2ascii
jdk rmic /usr/lib/jvm/java-6-sun/bin/rmic
jdk schemagen /usr/lib/jvm/java-6-sun/bin/schemagen
jdk serialver /usr/lib/jvm/java-6-sun/bin/serialver
jdk wsgen /usr/lib/jvm/java-6-sun/bin/wsgen
jdk wsimport /usr/lib/jvm/java-6-sun/bin/wsimport
jdk xjc /usr/lib/jvm/java-6-sun/bin/xjc
plugin xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
plugin mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
```I confess I don't fully understand what I see. Not all the files listed exist.

---

### Post by r-senior on 2011-03-17
You can confirm the version for the JRE by:

```
$ java -version
```

---

### Post by Paddy Landau on 2011-03-17
Thank you, got it now!
```
*java -version*
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)
```The Sun version.

---

