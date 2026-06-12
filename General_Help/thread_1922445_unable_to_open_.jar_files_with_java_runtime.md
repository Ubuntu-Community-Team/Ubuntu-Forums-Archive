---
title: "unable to open .jar files with java runtime"
date: 2012-02-08
forum: General Help
---

### Post by 3rdsurfer on 2012-02-08
the other day i realized for some, my icons for .jar files no longer open with java runtime. when i right click and go to "open with" it is not there, which mays me think it tried to update, but only did so partially, messing something up. but really im clueless. any ideas?

what i have tried:

[LIST]
[*]opening multiple .jar folders
[*]looking in both kde and unity
[*]checked for broken packages and updates (synaptic)
[*]updating from java 1.6._ to the version below
[/LIST]

ubuntu (11.10).

java -version output:
java version "1.7.0_02"
Java(TM) SE Runtime Environment (build 1.7.0_02-b13)
Java HotSpot(TM) 64-Bit Server VM (build 22.0-b10, mixed mode)

javac -version output
javac 1.7.0_02

---

### Post by brpylko on 2012-02-08
Sounds like a problem with your IcedTea installation, I would try apt-get purging it then re apt-get installing it.

If that does not work try right clicking on any jar file, choosing properties, then open with.

Try the first one first, this *could* be a sign of a broken installation of IcedTea.

---

### Post by morryis on 2012-02-28
Same problem here. purge-reinstall has no effect. Anything else having this problem?

---

### Post by drpjkurian on 2012-12-22
Hi
Iam using kde. I installed java JRE from software centre. To open .jar file, I right click the file and select "open with" select "other" A window pops up in which I navigate to /usr/bin/jexec. i save this option. Next time when i double click the .jar file, it opens.....

---

