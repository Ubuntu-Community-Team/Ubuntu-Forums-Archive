---
title: "tuxguitar not working on ubuntu 10.04"
date: 2010-05-10
forum: General Help
---

### Post by manav.g.garg on 2010-05-10
well i was using tuxguitar on 9.10 and it worked fine.. but it is not working on 10.04 since i have upgraded it... i tried to uninstall and then re install but it dint work.... nor does is show any error.. pls help

---

### Post by RubberChipmunk on 2010-05-13
I'm getting the same problem. Running tuxguitar from terminal returns this:

```
eric@eric-desktop:~$ tuxguitar 
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Control
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Control
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
	... 1 more
```

---

### Post by rbc on 2010-05-13
These folks seemed to have gotten it working again
[http://ubuntuforums.org/showthread.php?p=9096204](http://ubuntuforums.org/showthread.php?p=9096204)

---

### Post by noletolucas on 2011-07-08
Yeah, reinstalling the libswt libraries worked for me too.

Go to Synaptics, look for libswt, right click and "Mark for reinstall"

---

