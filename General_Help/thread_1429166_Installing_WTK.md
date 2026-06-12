---
title: "Installing WTK"
date: 2010-03-13
forum: General Help
---

### Post by Paper Tiger on 2010-03-13
Hi, 

I've downloaded and installed jdk-6u18-linux-i586.bin from Sun.  So I should have Sun Java SE installed.

I have downloaded and installed the Sun Java 6 runtime

Yet when I try to install the WTK it tells me it can't find a suitable java interpreter.

but - 

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice
[*], or type selection number: ^C
lawrence@lawrence-laptop:~/Downloads$ 

I have the path to the Sun JRE set as my default.  It didn't work with options 0 or 1 either, I tried.

The WTK is 2.5.2_01 - latest version from sun.

Has anyone got any suggestions?

ATM I'm considering a re-format and start over from scratch.  I'll stick with it, but so far I'm not having fun with Ubuntu (Karmic)

---

### Post by lykeion on 2010-03-14
Keep smiling...you're closer than you think :-)

What the installer asks for is the path to Java JDK (Developer Kit) not the JRE (Runtime Environment). This is what you need to develop midp applications with WTK. You could actually uninstall the JRE since this is included in the JDK.

Enter this path to point the installer to Sun Java JDK:

/usr/lib/jvm/java-6-sun/bin/

Hope this helps...

---

