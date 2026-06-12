---
title: "Eclipse not working (Ubuntu 12.04)"
date: 2012-09-13
forum: General Help
---

### Post by jmmeis13 on 2012-09-13
Hello, again.

I am having problem launching Eclipse on my Ubuntu. I installed it using the Ubuntu software center, and every time i launch it, it shows a launch image, and then shows me the message 

An error has occurred. See the log file
/home/janis/.eclipse/org.eclipse.platform_3.7.0_155965261/configuration/(random numbers).log.
 
And when i open it, it says 

!SESSION 2012-09-13 14:41:08.711 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_07
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2012-09-13 14:41:16.398
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-gtk-3740 in java.library.path
    no swt-gtk in java.library.path
    Can't load library: /home/janis/.swt/lib/linux/x86_64/libswt-gtk-3740.so
    Can't load library: /home/janis/.swt/lib/linux/x86_64/libswt-gtk.so

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

Please help, im trying to learn how to cod java, and i need this program to work, so that i can do the learning tutorial thingy.

Thanks, Janis

---

### Post by dawciobiel on 2012-09-13
Be sure you are using compatible system architecture, eclipse and java - all x64 bit.

sudo uname -a
java -version

---

### Post by Neoracu on 2012-09-13
Why don't you follow the instructions from [here]("http://developer.android.com/sdk/index.html"), is . very straight forward and the only thing you need to do is unpack the files to a place you want to.

For the SDK the installing instructions [here]("http://developer.android.com/sdk/installing/index.html")
Download for Eclipse [here]("http://www.eclipse.org/downloads/"). Just make sure you choose the right architecture, plus you will get the latest version for Eclipse which is not in the Ubuntu Repositories.

This is what I did, in case you find it useful:

I did unpack each of the downloaded files and placed it in my home folder, added a "dot" to hide them and created a launcher in my Cairo Dock to launch them.

For the Workspace made a folder called "Android" in my home folder and a "workspace" within.

As long as you choose the right Architecture for you system is very easy and the location of your folders may be wherever you want.

Best Regards

---

### Post by jmmeis13 on 2012-09-13
> **dawciobiel said:**
> Be sure you are using compatible system architecture, eclipse and java - all x64 bit.

sudo uname -a
java -version
Java says

java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) 64-Bit Server VM (build 23.3-b01, mixed mode)

and the other one says x86_64

---

### Post by jmmeis13 on 2012-09-13
> **Neoracu said:**
> Why don't you follow the instructions from [here]("http://developer.android.com/sdk/index.html"), is . very straight forward and the only thing you need to do is unpack the files to a place you want to.

For the SDK the installing instructions [here]("http://developer.android.com/sdk/installing/index.html")
Download for Eclipse [here]("http://www.eclipse.org/downloads/"). Just make sure you choose the right architecture, plus you will get the latest version for Eclipse which is not in the Ubuntu Repositories.

This is what I did, in case you find it useful:

I did unpack each of the downloaded files and placed it in my home folder, added a "dot" to hide them and created a launcher in my Cairo Dock to launch them.

For the Workspace made a folder called "Android" in my home folder and a "workspace" within.

As long as you choose the right Architecture for you system is very easy and the location of your folders may be wherever you want.

Best Regards
IM TRYING TO USE ECLIPSE FOR JAVA! Not android (facepalm). and i did the install using the download, and i completely ****** up ( im still quite often confused, how to install stuff from .tar.gz (i was only barely able to install java from .tar.gz))

---

### Post by jmmeis13 on 2012-09-13
Oh, and i forgot to say, but it did work yesterday, but it doesnt today

---

### Post by Ubunterrific on 2012-09-13
> **jmmeis13 said:**
> Java says

java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) 64-Bit Server VM (build 23.3-b01, mixed mode)

and the other one says x86_64

Hello, again! Solution is here: [http://stackoverflow.com/questions/10165693/ubuntu-eclipse-cannot-load-swt-libraries-not-opening](http://stackoverflow.com/questions/10165693/ubuntu-eclipse-cannot-load-swt-libraries-not-opening)

TLDR version: 
```

ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/
```(May need to be run as root)(and this command is for 64bit OS like yours)

So the problem seems to be that oracle java 7 puts the swt libraries in a place Eclipse doesn't check. Adding a symbolic link to them using the command above solves the problem in one command :D

---

### Post by jmmeis13 on 2012-09-13
> **Ubunterrific said:**
> Hello, again! Solution is here: [http://stackoverflow.com/questions/10165693/ubuntu-eclipse-cannot-load-swt-libraries-not-opening](http://stackoverflow.com/questions/10165693/ubuntu-eclipse-cannot-load-swt-libraries-not-opening)

TLDR version: 
```

ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/
```(May need to be run as root)(and this command is for 64bit OS like yours)

So the problem seems to be that oracle java 7 puts the swt libraries in a place Eclipse doesn't check. Adding a symbolic link to them using the command above solves the problem in one command :D


umm

janis@janis-HP-Pavilion-dv6700-Notebook-PC:~$ sudo ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/
[sudo] password for janis: 
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-atk-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-awt-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-cairo-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-glx-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-gnome-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-pi-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-webkit-gtk-3740.so': File exists

---

### Post by Ubunterrific on 2012-09-13
> **jmmeis13 said:**
> umm

janis@janis-HP-Pavilion-dv6700-Notebook-PC:~$ sudo ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/
[sudo] password for janis: 
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-atk-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-awt-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-cairo-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-glx-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-gnome-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-pi-gtk-3740.so': File exists
ln: failed to create symbolic link `/home/janis/.swt/lib/linux/x86_64/libswt-webkit-gtk-3740.so': File exists


hmmm
Let me have a think first - there's the option of forcibly deleting all the libswt files in the x86_64 folder but for now, you could try
```

sudo update-alternatives --config java 
```

see which java type is set as the default and try switching to another one, then try eclipse and report back. :(

---

### Post by Ubunterrific on 2012-09-13
> **jmmeis13 said:**
> (i was only barely able to install java from .tar.gz))

wait a sec...you installed java from a tar.gz ? I thought you were using the version from the webupd8 java ppa? 
The problem could be that the files in /home/janis/.swt/lib/linux/x86_64/ don't have the right permissions then and then eclipse complains because it sees them but can't run them.

---

### Post by jmmeis13 on 2012-09-13
> **Ubunterrific said:**
> hmmm
Let me have a think first - there's the option of forcibly deleting all the libswt files in the x86_64 folder but for now, you could try
```

sudo update-alternatives --config java 
```see which java type is set as the default and try switching to another one, then try eclipse and report back. :(

Hey, i changed from the oficial java i had (jdk1.7.0_07) and switched to openjdk 7, and it works! thanks! now im just gonna have to switch between javas, because i like to use the official java, instead of openjdk

---

### Post by jmmeis13 on 2012-09-13
> **Ubunterrific said:**
> hmmm
Let me have a think first - there's the option of forcibly deleting all the libswt files in the x86_64 folder but for now, you could try
```

sudo update-alternatives --config java 
```see which java type is set as the default and try switching to another one, then try eclipse and report back. :(
thanks, worked. I just wanna know, can you like somehow tell me, how to make a desktop terminal app? i wanna make a little shortcut on my desktop, which opens terminal and types the sudo update-alternatives --config java code, is there an easy way to do that?

---

