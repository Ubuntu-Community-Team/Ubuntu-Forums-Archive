---
title: "Installing BlueJ"
date: 2006-03-22
forum: General Help
---

### Post by rossjman1 on 2006-03-22
I've downloaded the .jar file from [http://bluej.org/download/download.html](http://bluej.org/download/download.html), but I get this error when I try to run it:
```
jeff@ubuntu:~$ java -jar bluej-211.jar
Exception during event dispatch:
java.lang.NullPointerException
   at javax.swing.text.JTextComponent$CaretBlinkTimer.actionPerformed(java.awt.event.ActionEvent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.Timer.fireActionPerformed(java.awt.event.ActionEvent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.Timer.fireActionPerformed() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.Timer.drainEvents() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.Timer$1.run() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.event.InvocationEvent.dispatch() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.dispatchEvent(java.awt.AWTEvent) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventDispatchThread.run() (/usr/lib/libgcj.so.6.0.0)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.5.so)

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted
jeff@ubuntu:~$

```
As my computer is too slow to run Eclipse, and since we use BlueJ in school, much help is appreciated.

---

### Post by rossjman1 on 2006-03-22
bump

---

### Post by adamkane on 2006-03-23
Reference:
[http://www.zoia.org/blog/archives/2006/01/09/bluej-en-ubuntu-breezy/]("http://www.zoia.org/blog/archives/2006/01/09/bluej-en-ubuntu-breezy/")
[https://wiki.ubuntu.com/RestrictedFormats#java]("https://wiki.ubuntu.com/RestrictedFormats#java")

Add the universe and multiverse repositories, if you haven't already:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

Install fakeroot and java-package:

```

sudo apt-get install fakeroot java-package

``` 
Download J2SE Development Kit 5.0 Update 6 (Linux Platform) to your desktop:
[http://java.sun.com/j2se/1.5.0/download.jsp]("http://java.sun.com/j2se/1.5.0/download.jsp")

```

cd ~/Desktop
fakeroot make-jpkg jdk-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2sdk1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java

``` 
Select:
/usr/lib/j2sdk1.5-sun/bin/java

Download BlueJ to your desktop and install:
[http://www.bluej.org/download/download.html]("http://www.bluej.org/download/download.html")

```

cd ~/Desktop
sudo java -jar bluej-212.jar

``` 
BlueJ will ask you where to install. I chose: 
/usr/local/bluej

```

cd /usr/bin
sudo ln -s /usr/local/bluej/bluej
bluej

``` 
More Ubuntu Java installation info:
[https://wiki.ubuntu.com/RestrictedFormats#java]("https://wiki.ubuntu.com/RestrictedFormats#java")
 
You can install Java SDK with Automatix:
[http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29]("http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29")

or by adding the Sevea repository:
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")
```

sudo apt-get install sun-j2sdk1.5

```

---

### Post by rossjman1 on 2006-03-23
Thank you, it worked perfectly.

---

### Post by lilolpete on 2006-04-13
-_- having major hard time installing bluej for some reason. I got Automatix to install both SDK and JRE. After all that, i go to terminal to do cd ~/Desktop then java -jar bluej-212.jar but when its pops up and tells me to locate the "tools.jar" file Bluej cant' look into the files. I'll bring up /usr/lib/j2sdk1.5-sun/lib and it doesnt' see the jar file. Someone please help me out here. ](*,)

---

### Post by adamkane on 2006-04-21
I updated the instructions to install to /usr/local/bluej. This should make things a bit simpler for everyone.

When installing bluej, don't browse to the installation directory. Just type in the following info:

Directory to install to: /usr/local/bluej
Java (JDK) directory: /usr/lib/j2sdk1.5-sun

---

