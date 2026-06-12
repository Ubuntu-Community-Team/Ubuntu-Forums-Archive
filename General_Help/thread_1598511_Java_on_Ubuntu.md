---
title: "Java on Ubuntu"
date: 2010-10-16
forum: General Help
---

### Post by Bv202 on 2010-10-16
Hi,

I'm completely new to Linux, so please bear with me :)

At school, we have to use some silly Java IDE called BlueJ, which didn't work on Ubuntu (my code didn't compile with no errors). I've found on the support site BlueJ has problems with openJDK and suggested to remove it and install sun-java6-jdk instead. I did this and it worked fine.

Today I wanted to play Minecraft. The game runs, but once I try to start a new game it crashes with this output:
> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb76f7424, pid=5495, tid=1453828976
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (17.0-b16 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9
# Distribution: Ubuntu maverick (development branch), package 6b20-1.9-0ubuntu1
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/bjorn/Bureaublad/hs_err_pid5495.log
[thread 1778367344 also had an error]
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Afgebroken


I don't know what the difference between OpenJDK-6-jre/sun-jave6-jre is, but I thought removing OpenJDK-6-jre and installing sun-java6-jre might solve the problem, just like it did with BlueJ (but now trying the other JRE instead of the JDK). 

But when I try to run the game again after doing this, I'm getting this:
> Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1649)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1750)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1667)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Component.<clinit>(Component.java:572)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)


Could anyone please explain me what the difference between openjdk/openjdk-6-jre/sun-java6-jdk/sun-java6-jre is and if there is a way to get this game to work?

Thanks

---

### Post by CoreyB. on 2010-10-16
> **Bv202 said:**
> Hi,

I'm completely new to Linux, so please bear with me :)

At school, we have to use some silly Java IDE called BlueJ, which didn't work on Ubuntu (my code didn't compile with no errors). I've found on the support site BlueJ has problems with openJDK and suggested to remove it and install sun-java6-jdk instead. I did this and it worked fine.

Today I wanted to play Minecraft. The game runs, but once I try to start a new game it crashes with this output:


I don't know what the difference between OpenJDK-6-jre/sun-jave6-jre is, but I thought removing OpenJDK-6-jre and installing sun-java6-jre might solve the problem, just like it did with BlueJ (but now trying the other JRE instead of the JDK). 

But when I try to run the game again after doing this, I'm getting this:


Could anyone please explain me what the difference between openjdk/openjdk-6-jre/sun-java6-jdk/sun-java6-jre is and if there is a way to get this game to work?

Thanks

It looks like you are still using openjdk, are you sure you have uninstalled it?  Try running:

sudo update-java-alternatives -s java-6-sun

in Terminal.

OpenJdk is an open source implementation of Java.  Sun java is the regular official java.  The -jre ones just have the runtime environment.

Let me know if this works or doesn't work.

---

### Post by Bv202 on 2010-10-16
Hey,

Doesn't work :(

Whatever applet I try to run, I get this error:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb76ef424, pid=10071, tid=2789411696
#
# JRE version: 6.0_21-b06
# Java VM: Java HotSpot(TM) Server VM (17.0-b16 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#


I've tried OpenJDK, Sun Java and even downloaded the most recent version from sun.com - I keep getting that error.

---

### Post by Bv202 on 2010-10-16
Hey,

It seems this is related to some graphics drivers. I've removed "fglrx" and now everything runs fine.

Wat is fglrx used for? Because it seems I can still use OpenGL etc.

---

### Post by Bv202 on 2010-10-16
Now I'm getting REALLY frustrated.

Reinstalled fglrx... now the OS doesn't boot anymore -.-

Just some stupid black screen...

Is there some way to reinstall these drivers via the live cd? Or make my system at least a bit USABLE again?

EDIT:
It's booting again.. I've re-installed the drivers via the recovery mode. But now I have the same problem again as in the beginning...

---

### Post by bgilbert on 2010-10-31
Any luck with this issue?

I'm having the exact same problem, and haven't been able to figure out any solution. I'm using an Radeon HD 5730, and removing the proprietary fglrx drivers are not really an option for me.

Created this post on the support section of the minecraft forum:

[http://www.minecraftforum.net/viewtopic.php?f=17&t=69269](http://www.minecraftforum.net/viewtopic.php?f=17&t=69269)

But, I've only really gotten the 'update your drivers or don't use ubuntu' response.

---

### Post by scouser73 on 2010-10-31
I'm unsure if you're after installing the Java Runtime Environment or not, if you are, then please follow the instructions on this website: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by ms4py on 2010-12-01
Getting the same error with Scilab, see this log for details:
[http://paste.pocoo.org/show/298758/](http://paste.pocoo.org/show/298758/)

---

### Post by f0ku5 on 2011-02-13
I am also having this problem.  Using Ubuntu 10.10 Maverick.

Tested with OpenJDK, Sun Java 1.6.0_23 and 1.6.0_22.

Video card is an ATI Radeon HD4870 (rv770).

Tried fglrx 2:8.780-0ubuntu2 as well as the driver directly from ATI:
ATI Catalyst™ 11.1 Proprietary Linux x86 Display Driver

No luck.

---

### Post by f0ku5 on 2011-02-13
I have resorted to using the open-source drivers, and they seem to work reasonably well.

---

