---
title: "someone convert my .bat file?"
date: 2011-03-27
forum: General Help
---

### Post by kolmad on 2011-03-27
hello my friend made a private server and it runs with a bat file can you convert it?
code:
@echo off
java -cp bin;lib/clientlibs.jar client 0 live english game0
pause

---

### Post by kolmad on 2011-03-27
bump

---

### Post by fela on 2011-03-27
> **kolmad said:**
> hello my friend made a private server and it runs with a bat file can you convert it?
code:
@echo off
java -cp bin;lib/clientlibs.jar client 0 live english game0
pause

```
#!/bin/bash
java -cp bin/lib/clientlibs.jar client 0 live english game0
```

Save it as nameofbat.sh, make sure it's executable.

---

### Post by kolmad on 2011-03-27
it didnt work anyway to make it a .jar or .exe file?

---

### Post by fela on 2011-03-27
> **kolmad said:**
> it didnt work anyway to make it a .jar or .exe file?

If the bat worked, then it is already a .jar file....

What files and directories are there in the same directory as the bat file?

---

### Post by kolmad on 2011-03-27
folders: bin; cache; lib; src
files: build.bat; itemlist.jar; jagex_runescape_preferences2.dat; run.bat<one i need open; and run.sh<the one i made

---

### Post by fela on 2011-03-27
Hi
When you ran run.sh, was your current directory the directory of the game?

---

### Post by kolmad on 2011-03-28
idk

---

### Post by fela on 2011-03-29
> **kolmad said:**
> idk

OK, well open a terminal, cd to the directory contaning run.sh, and do
```
sh ./run.sh
```

Should work.

---

### Post by kolmad on 2011-03-29
when i do that i get this
java.lang.ClassNotFoundException: client
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: client. Program will exit.

---

### Post by fela on 2011-03-29
Do you have Java (JRE) installed on your system?

---

### Post by kolmad on 2011-03-30
I got it and nothing else happened it did the same thing

---

### Post by DaithiF on 2011-03-30
java -cp bin[COLOR=Red]**;**[/COLOR]lib/clientlibs.jar client 0 live english game0

---

### Post by fela on 2011-03-30
> **DaithiF said:**
> java -cp bin[COLOR=Red]**;**[/COLOR]lib/clientlibs.jar client 0 live english game0

Ah, didn't spot that :lolflag:

---

### Post by DaithiF on 2011-03-30
actually make that:
```
java -cp bin:lib/clientlibs.jar client 0 live english game0

```semi-colon on windows, colon on *nix ... otherwise bash would treat ; as a command delimiter

---

### Post by kolmad on 2011-03-31
thanks soo much!

---

