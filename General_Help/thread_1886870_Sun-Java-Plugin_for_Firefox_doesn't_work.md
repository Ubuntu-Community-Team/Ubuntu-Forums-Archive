---
title: "Sun-Java-Plugin for Firefox doesn't work"
date: 2011-11-25
forum: General Help
---

### Post by slabo on 2011-11-25
Ubuntu 11.04 amd64 here. I installed sun-java6-bin, sun-java6-jre and sun-java6-plugin and checked via update-alternatives that they are used. On first glance, it looks alright: java -version says i'm using 6.0_26-b03, Firefox says on the about:plugin-page that i'm using the sun-java plugin, but the [Java test-page]("http://java.com/en/download/testjava.jsp") doesn't work. Also, the online-application i installed this for doesn't work. jcontrol crashes.

Also, my "Sun Java Plugin Control"-Application doesn't work.

The weird thing is that i installed Sun Java yesterday, and it worked. (Can only say this for the online-application, though.) Today after booting my computer anew, it didn't work. Since then, i deinstalled openjdk and reinstalled it (since i need java) and also reinstalled sun-java, but can't get it to run.

Any ideas would be greatly appreciated.

---

### Post by sammiev on 2011-11-25
Try [this]("http://sites.google.com/site/easylinuxtipsproject/java") it works for everyone else. :)

---

### Post by oldtimer7777 on 2011-11-25
Did you install Java from the PPA? 

> **slabo said:**
> Ubuntu 10.04 amd64 here. I installed sun-java6-bin, sun-java6-jre and sun-java6-plugin and checked via update-alternatives that they are used. On first glance, it looks alright: java -version says i'm using 6.0_26-b03, Firefox says on the about:plugin-page that i'm using the sun-java plugin, but the [Java test-page]("http://java.com/en/download/testjava.jsp") doesn't work. Also, the online-application i installed this for doesn't work. jcontrol crashes.

Also, my "Sun Java Plugin Control"-Application doesn't work.

The weird thing is that i installed Sun Java yesterday, and it worked. (Can only say this for the online-application, though.) Today after booting my computer anew, it didn't work. Since then, i deinstalled openjdk and reinstalled it (since i need java) and also reinstalled sun-java, but can't get it to run.

Any ideas would be greatly appreciated.

---

### Post by slabo on 2011-11-25
Installed it via Synaptic.

sammiev, will have a look at it and report, thx.

---

### Post by slabo on 2011-11-25
Okay, so i tried it, and the Plugin is, as before, listed on "about:plugins", but it doesn't work, according to the [Java test-page]("http://java.com/en/download/testjava.jsp"). Also, when trying to start the Control Panel i get:

```
slabo@ubuntu:~/.mozilla/plugins$ /opt/java/64/jre1.6.0_29/bin/ControlPanel
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f2aec965726, pid=12448, tid=139821898569472
#
# JRE version: 6.0_29-b11
# Java VM: Java HotSpot(TM) 64-Bit Server VM (20.4-b02 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libc.so.6+0x32726]  char+0x16
#
# An error report file with more information is saved as:
# /home/slabo/.mozilla/plugins/hs_err_pid12448.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/opt/java/64/jre1.6.0_29/bin/ControlPanel: Zeile 135: 12448 Abgebrochen             ${java_home}/java -Djavaplugin.user.profile=${USER_JPI_PROFILE} -Xbootclasspath/a:${java_home}/../lib/deploy.jar ${_JAVA_VM_OPTIONS} com.sun.deploy.panel.ControlPanel

```

"java -version" works.

---

### Post by sammiev on 2011-11-25
Make sure you have the restricted extras installed. :)

---

