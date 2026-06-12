---
title: "linux mine craft crash"
date: 2011-01-04
forum: General Help
---

### Post by mmsmc on 2011-01-04
does anybody have a clue what this means, ive been searching around but have found nothing useful       Minecraft has crashed!             ----------------------        Minecraft has stopped running because it encountered a problem.  If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email]. Please include a description of what you did when the error occured.    --- BEGIN ERROR REPORT a1dce528 -------- Generated 1/4/11 2:53 PM  Minecraft: Minecraft Beta 1.1_02 OS: Linux (i386) version 2.6.35-24-generic Java: 1.6.0_20, Sun Microsystems Inc. VM: OpenJDK Server VM (mixed mode), Sun Microsystems Inc. LWJGL: 2.4.2 [failed to get system properties (java.lang.NullPointerException)]  java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time. 	at org.lwjgl.opengl.Display.create(Display.java:846) 	at org.lwjgl.opengl.Display.create(Display.java:784) 	at org.lwjgl.opengl.Display.create(Display.java:765) 	at net.minecraft.client.Minecraft.a(SourceFile:279) 	at net.minecraft.client.Minecraft.run(SourceFile:641) 	at java.lang.Thread.run(Thread.java:636) --- END ERROR REPORT 3996e734 ----------

---

### Post by WorMzy on 2011-01-04
It means there's a bug in the program, and you've encountered it. It is only a beta after all.

Do what the message says or just carry on playing. If the error is preventing you from doing anything, then try reinstalling minecraft and/or deleting your config (~/.minecraft).

---

### Post by mmsmc on 2011-01-04
thanks, it works

---

### Post by mmsmc on 2011-01-04
one more problem, this crash now occurs when i load it as a program(executable jar(double click on icon)) and is extemely laggy when i call the program from the terminal  heres some more info, i recently got a comp crash caused by my nvidia drive, i had to reset my graphics to default mode because it would put me into tty mode and no desktop, hope this helps

---

### Post by mmsmc on 2011-01-04
is it that i am missing a nvidia driver?

---

### Post by mmsmc on 2011-01-04
infact when i run it through terminal it makes my entire computer laggy, but no problem before crash


this is a screen shot of what the terminal says if it is any help

---

### Post by I8NY on 2011-01-15
try getting "sun-java6-*" instead of the OpenJDK it is worth a try.  I have never had problems with minecraft expect for big TNT explosions.

---

