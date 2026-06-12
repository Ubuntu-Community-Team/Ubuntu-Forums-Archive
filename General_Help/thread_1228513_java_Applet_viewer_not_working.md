---
title: "java Applet viewer not working"
date: 2009-08-01
forum: General Help
---

### Post by yogi4 on 2009-08-01
Hi m using ubuntu 9.04 i hd installed sun jdk & jre from the bin file, i already have open jdk & jre.
most of my .java files compiles & run fine in terminal
bt i cant start applet viewer with it .
when i type appletviewer Filename.java terminal shows-
The program 'appletviewer' can be found in the following packages:
 * openjdk-6-jdk
 * java-gcj-compat-dev
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: appletviewer: command not found

on running it on firefox it shows applet box bt shows applet cant initialize.I had made sure that i type the right code bt to no use.

I hd reinstalled everything bt still prob persist.

Please

---

### Post by mthalis on 2009-08-01
Are you set java path properly, read this
[http://ubuntuforums.org/showthread.php?t=217936](http://ubuntuforums.org/showthread.php?t=217936)

---

### Post by yogi4 on 2009-08-01
i had already set the class path & variable that why rest of d java programms r able to compile & run , d problem is only wid applets!!

---

### Post by yogi4 on 2009-08-01
pls someone help me in this regard

---

### Post by yogi4 on 2009-08-01
pls help me oderwise m thinking of reinstalling ubuntu

---

### Post by sandeepjshenoy on 2009-08-02
Goto to synaptic package manager and search for "jre". Remove all installed versions of java. Now install the following:
sun-java6-jre
sun-java6-bin
sun-java6-fonts
sun-java6-plugin

This should do the trick!

---

### Post by yogi4 on 2009-08-03
I had  done that too
i hd done every think i cn 
even hd reinstalled jdk @_@

---

### Post by yogi4 on 2009-08-06
Well i hd a fresh installation of ubuntu bt m still facing d same prob :(

---

