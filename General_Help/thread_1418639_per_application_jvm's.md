---
title: "per application jvm's"
date: 2010-02-28
forum: General Help
---

### Post by MightierMouse on 2010-02-28
I'm trying to run a couple of Java programs that each run best in a different virtual machine. One of them doesn't seem to run at all inside an openjdk jvm with the Awesome Window Manager running. The other will run best if I employ a fix that only works on openjdk jvm's. I have the sun jre set as my virtual machine, and I would like to use openjdk for the other one. Here's the script I've used to try to get the program running with the openjdk jvm:

#!/bin/bash
cd $HOME/GoGrinder
_JAVA_AWT_NONREPARENTING=1 /usr/lib/jvm/java-6-openjdk/jre/bin/java -jar GoGrinder.jar

And here is the output I get when I run the script:
 
$ bin/GoGrinder.sh 
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1664)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
	at java.awt.Color.<clinit>(Color.java:279)
	at GoGrinder.Main.<clinit>(Main.java:50)
Could not find the main class: GoGrinder.Main. Program will exit.

This is a program that I've run many times on metacity using the openjdk (I only installed the sun jdk recently). What am I doing wrong here and what is the procedure for running different JVM's on a per-application basis?

---

### Post by MightierMouse on 2010-03-02
*Bump*

---

