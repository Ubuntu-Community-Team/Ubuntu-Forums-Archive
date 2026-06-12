---
title: "Java Issues While Opening Limewire"
date: 2010-01-13
forum: General Help
---

### Post by pelosm on 2010-01-13
I am having trouble opening limewire after instalation the error I get is:

Errors were encountered while processing:
 sun-j2sdk1.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
eddie@eddie-desktop:~$ limewire
bash: /usr/bin/limewire: No such file or directory
eddie@eddie-desktop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: no splashscreen in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1678)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.SplashScreen.getSplashScreen(SplashScreen.java:111)
    at org.limewire.ui.swing.Main.main(Main.java:32)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.6+)
The version of Java in your PATH is:
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)


I tried reinstalling java but nothing.. 
thank you

---

