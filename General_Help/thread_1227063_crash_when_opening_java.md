---
title: "crash when opening java"
date: 2009-07-30
forum: General Help
---

### Post by gleft on 2009-07-30
hi guys, i have a problem, when i open jdownloader with java the screen disappears for a second and then all i see is fragments of the open windows. i can move the mouse and i have to shut down and restart. do you know what may be tha problem?

---

### Post by Mighty_Joe on 2009-07-30
Which version of java are you using?
```
java -version
```

If you are not using the Sun JRE, I'd recommend installing it. You also have to tell Ubuntu to use Sun Java with [these steps]("https://help.ubuntu.com/community/Java").

---

### Post by gleft on 2009-07-30
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08 ) 
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
this is the version i use

---

### Post by Mighty_Joe on 2009-07-30
That version seems fine.  Try running JDownloader from the command line.  In a terminal, CD to the directory where you installed JDownloader and invoke:
```
java -jar JDownloader.jar
```
JDownloader prints a lot of debug information to the console.  Hopefully we'll see an exception stack trace to see what's going wrong.

---

