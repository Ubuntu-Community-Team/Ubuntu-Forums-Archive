---
title: "Eclipse is unable to run"
date: 2012-05-10
forum: General Help
---

### Post by kensclark15 on 2012-05-10
When I run Eclipse (I use XFCE for my desktop), I get this error in a log file: 
```
!SESSION 2012-05-10 16:25:04.690 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_04
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2012-05-10 16:25:06.884
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-gtk-3740 in java.library.path
    no swt-gtk in java.library.path
    Can't load library: /home/kensclark15/.swt/lib/linux/x86_64/libswt-gtk-3740.so
    Can't load library: /home/kensclark15/.swt/lib/linux/x86_64/libswt-gtk.so

    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:285)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
    at org.eclipse.swt.internal.C.<clinit>(C.java:21)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
    at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:695)
    at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
    at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:153)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:95)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:601)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1386)
```

---

### Post by sefs on 2012-05-10
I see you seem to be using Oracle Java 7, although the recommended version is Oracle Java 6.  

Have you tried using it with oracle java 6 or even the open jdk?

Might want to post this in the programming sub forum as it would probably be better answered there.

Did you see this thread also?
[http://ubuntuforums.org/showthread.php?p=11895062](http://ubuntuforums.org/showthread.php?p=11895062)

---

### Post by ammofreak on 2012-05-10
Hi ):P

Possibly you are running Eclipse 64 bit with Java 32 bit???...:)

---

### Post by roosh on 2012-05-18
I got the same error after installing Oracle's java-6 from their website and changing my default java.

I don't know how to fix it thought :confused:

---

### Post by roosh on 2012-05-18
Update: Using > sudo update-alternatives --config java and choosing openjdk6 lets eclipse work again (but forces me to use openjdk as default)

---

### Post by roosh on 2012-05-19
So it seems that if I switch back to Sun Java 6 as default, Eclipse no longer works unless I tell Eclipse to use openjdk:

```
eclipse -vm /usr/lib/jvm/java-6-openjdk/bin/
```

Any help on how to get this fixed?

---

### Post by hetodd on 2012-07-13
From another site...

on my Ubuntu 12.04 32 bit. I edit the command to:

```
ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86/
```

And on Ubuntu 12.04 64 bit try:

```
ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/
```

It worked for me.

---

### Post by MankindDotCom on 2012-07-18
The symbolic link worked for me as well. (re: hetodd)
(Oracle java-7, Ubuntu 12.04 LTS, following [Web UDP8 install instructions]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html").)

---

