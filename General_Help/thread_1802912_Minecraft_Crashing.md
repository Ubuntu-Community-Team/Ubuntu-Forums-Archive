---
title: "Minecraft Crashing"
date: 2011-07-12
forum: General Help
---

### Post by sscot600 on 2011-07-12
Hello
Ive recently switched from XP to ubuntu and I am trying to get my minecraft to work for the past few days and have had no luck.  It always crashes right after I log in.  I have tried replacing the lwjgl files and native things but that hasn't gotten me anywhere.  Also, I have installed all the required java runtime environment.  When I launch the minecraft.jar file through terminal, i get this error message: 

stephen@Dewey:~$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
java.io.FileNotFoundException: /home/stephen/.minecraft/lastlogin (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at net.minecraft.LoginForm.readUsername(LoginForm.java:131)
    at net.minecraft.LoginForm.<init>(LoginForm.java:76)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:30)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)  <------ thats supposed to be :158 ), stupid smile face
16 achievements
151 recipes
Setting user: sscot600, -5030658791383350217
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x08591824, pid=4563, tid=2999544688
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK Client VM (20.0-b11 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.10.2
# Distribution: Ubuntu 11.04, package 6b22-1.10.2-0ubuntu1~11.04.1
# Problematic frame:
# C  [libGL.so.1+0x79824]  XF86DRIQueryExtension+0x8e
#
# An error report file with more information is saved as:
# /home/stephen/hs_err_pid4563.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted


Any help will be greatly appreciated!!

---

### Post by gandaran on 2011-07-12
are you using openjdk-java or sun-java?

---

### Post by sscot600 on 2011-07-12
sun java

---

### Post by sscot600 on 2011-07-12
OK i just got it to start without crashing but it instantly gave me this error:


      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 7/12/11 5:54 PM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (i386) version 2.6.38-8-generic
Java: 1.6.0_24, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.7.1
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not choose GLX13 config
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:717)
    at org.lwjgl.opengl.Display.create(Display.java:855)
    at org.lwjgl.opengl.Display.create(Display.java:785)
    at org.lwjgl.opengl.Display.create(Display.java:766)
    at net.minecraft.client.Minecraft.a(SourceFile:294)
    at net.minecraft.client.Minecraft.run(SourceFile:716)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 889c753a ----------

---

### Post by WorMzy on 2011-07-12
> **gandaran said:**
> are you using openjdk-java or sun-java?

> **sscot600 said:**
> sun java

> **sscot600 said:**
> # Java VM: **OpenJDK** Client VM (20.0-b11 mixed mode, sharing linux-x86 )

Afraid not. ;)

If you installed sun java, make sure to run

```
sudo update-alternatives --config java
```

---

