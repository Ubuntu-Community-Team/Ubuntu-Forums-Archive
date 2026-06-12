---
title: "Java Crashes on: Win7 Partition, Wine, Linux Ubuntu 11.10"
date: 2012-01-29
forum: General Help
---

### Post by codya517 on 2012-01-29
Java has never worked that well since I switched to Ubuntu from Win7. In order to run things like minecraft i had to download the windows copy and run it through wine, wine would spit out some java errors but eventually work. Now it does not at all and most of java's functionality seems to be broken. I've reinstalled Java a few times and different ways. I installed Sun Java through the repos with apt-get and installed it manually from the bin file from sun java's website. To no avail java still is broken no matter how many times i remove it and reinstall it. Furthermore the java wine uses (which is a windows java isntalled by wine) ceases to work entirely now. I logged onto my win7 partition and noticed java suddenly is broken on there as well. I've even tried OpenJDK to get things working natively.

As far as java on linux goes, the first error I get is "no file or directory called javaw" which is windows java. That doesn't make sense. I've been fittling around with it and using minecraft (linux package) to test if java is working. Basically minecraft crashes after log in when entering the world. Here are the errors that I get when trying to run minecraft natively under linux.

java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(Unknown Source)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(Unknown Source)
	at java.lang.ProcessImpl.start(Unknown Source)
	... 2 more
27 achievements
174 recipes
Setting user: *********, 6526187482246182101
Loading: net.java.games.input.LinuxEnvironmentPlugin
INSTANCE.absAxesIDs is only 63 long, so 63 not contained
INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 8 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7714416, pid=2533, tid=2381081456
#
# JRE version: 6.0_30-b12
# Java VM: Java HotSpot(TM) Server VM (20.5-b03 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# An error report file with more information is saved as:
# /home/****/hs_err_pid2533.log
[thread -1950307472 also had an error]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted

I've already tried a symlink to javaw. it just hides the errors and the crashes continue. I've reinstalled and redownloaded minecraft already, at first i thought it was confused abotu what OS I have until I noticed java crashes were happening basically across the board.

Any help appreciated.

---

### Post by codya517 on 2012-01-31
No one? :(

---

