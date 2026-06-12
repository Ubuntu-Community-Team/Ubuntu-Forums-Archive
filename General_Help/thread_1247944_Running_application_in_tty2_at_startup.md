---
title: "Running application in tty2 at startup"
date: 2009-08-23
forum: General Help
---

### Post by bferd on 2009-08-23
Hi I already posted a similar thread [here]("http://ubuntuforums.org/showthread.php?t=1246193") but it was in the server category and I hoped more people would see it here.

I want to have Azureus start in tty2 at startup and am unsure how to do it. Azureus starts in command line mode using:

```
$ java -jar /usr/share/java/Azureus2.jar --ui=console
```

and I can get it to run at startup using the Webmin Bootup and Shutdown script:

```
#!/bin/sh
java -jar /usr/share/java/Azureus2.jar --ui=console
```

I'd like to get this running in tty2 if possible.

Any help is appreciated.

---

### Post by voxel on 2009-09-26
Bump! I'm having the same problem. I would really like to know how to start a script in tty2

---

