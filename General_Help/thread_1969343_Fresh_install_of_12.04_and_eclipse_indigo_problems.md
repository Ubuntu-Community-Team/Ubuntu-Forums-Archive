---
title: "Fresh install of 12.04 and eclipse indigo problems"
date: 2012-04-29
forum: General Help
---

### Post by niranjan_rao on 2012-04-29
I have fresh install of ubuntu 12.04 32bit along with sun jdk 1.7 and eclipse indigo.

Eclipse starts fine and seems to be working ok, but anytime I switch to different tab, it dies. No information in logs either. 

Any ideas what's going on? Can try to triage it as much as possible if someone tells me what needs to be done

---

### Post by linuxxe on 2012-05-01
SOLVED

I've a similar problem, random crash when refactoring, saving files, opening new class and many other cases.
Plus, a systematical crash when opening a windowbuilder visual editor.
<strike>I can't find log,too. I've searched for hs_err* on the entire filesystem and the eclipse log file did not report problems</strike>.

Log founded in .Xsession_error with a PermGenException, I've  tried a higher value for vm args. Windowbuilder now seems to work.

Software affected:
Ubuntu 12.04 LTS 64bit (update from previous version)
Eclipse Indigo (latest update, with many plug-in)
java sun JDK 1.7.0_02 64Bit

processor: intel E8550
RAM: 8GB

Thx

---

### Post by cazazo on 2012-05-01
I'm having issues as well. I don't believe it's because of Java once Netbeans is working fine! In my case it's crashing on start up! Here is the log generated:


!SESSION 2012-05-02 00:37:38.071 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_03
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_AU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2012-05-02 00:37:38.711
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
	no swt-gtk-3740 in java.library.path
	no swt-gtk in java.library.path
	Can't load library: /home/cazazo/.swt/lib/linux/x86/libswt-gtk-3740.so
	Can't load library: /home/cazazo/.swt/lib/linux/x86/libswt-gtk.so

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

More info:

:~$ update-alternatives --list java
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
/usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
/usr/lib/jvm/java-7-oracle/bin/java


~$ sudo update-alternatives --config java
[sudo] password for cazazo: 
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-oracle/bin/java             1062      auto mode
  1            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode
* 3            /usr/lib/jvm/java-7-oracle/bin/java             1062      manual mode

Press enter to keep the current choice[*], or type selection number: 3

---

### Post by r-senior on 2012-05-01
> **cazazo said:**
> I'm having issues as well ...

java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
	no swt-gtk-3740 in java.library.path
	no swt-gtk in java.library.path
	Can't load library: /home/cazazo/.swt/lib/linux/x86/libswt-gtk-3740.so
	Can't load library: /home/cazazo/.swt/lib/linux/x86/libswt-gtk.so

Are you sure that's the same issue as the OP? Does your Eclipse start at all? SWT is the UI toolkit that Eclipse uses throughout.

What do you get if you run this command?

```
ls -R ~/.swt
```

And what architecture is your machine?

```
uname -m
```

---

### Post by cazazo on 2012-05-01
Based on the error in the Logs....
the problem was
:
Can't load library: /home/cazazo/.swt/lib/linux/x86/libswt-gtk-3740.so
Can't load library: /home/cazazo/.swt/lib/linux/x86/libswt-gtk.so

I went to terminal and entered
~$ locate libswt-gtk-3740.so
It did return the path of the file
I copied over to the folder above (/home/cazazo/.swt/lib/linux/x86/libswt-gtk-3740.so
)
Eclipse started just fine!
Hope that helps!

---

### Post by r-senior on 2012-05-01
Good!

Where was it, out of interest?

---

### Post by snailteaser on 2012-05-06
I have had similar issues but after I copied one .so file over to where Eclipse was expecting it, it always errored out for a different one.

So instead of going through all these, I just created a link to /usr/lib/jni where all these .so files appear to reside

[EMAIL="user@UbuntuMachine:%7E/.swt"]user@UbuntuMachine:~/.swt[/EMAIL]/lib/linux$ rm -rf x86
[EMAIL="user@UbuntuMachine:%7E/.swt"]user@UbuntuMachine:~/.swt[/EMAIL]/lib/linux$ ln -s /usr/lib/jni x86
[EMAIL="user@UbuntuMachine:%7E/.swt"]user@UbuntuMachine:~/.swt[/EMAIL]/lib/linux$ ls -al
total 8
drwxr-xr-x 2 user usergroup 4096 May  6 09:08 .
drwxr-xr-x 3 user usergroup 4096 Dec 24 23:57 ..
lrwxrwxrwx 1 user usergroup   12 May  6 09:08 x86 -> /usr/lib/jni

it looks like working just now.

---

### Post by zedabota on 2013-02-08
Hello, im a newbi in linux, but im trying to use my tools under ubunto but i just cant start eclipse 3 days of strugling ang googling "no go"
i get this erros over and ocer again
!SESSION 2013-02-08 23:56:52.184 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_13
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=pt_PT
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2013-02-08 23:56:56.859
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-pi-gtk-3740 in java.library.path
    no swt-pi-gtk in java.library.path
    Can't load library: /home/joao/.swt/lib/linux/x86/libswt-pi-gtk-3740.so
    Can't load library: /home/joao/.swt/lib/linux/x86/libswt-pi-gtk.so

    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:285)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
    at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
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

---

### Post by Marthewicked on 2013-02-13
I would like to know this as well very much.  I even would like to know if i can start over from scratch if that will fix the problem, install java and eclipse.   don't even need eclipse either.

---

