---
title: "error when running .sh files"
date: 2009-12-13
forum: General Help
---

### Post by gschier on 2009-12-13
I have an sh file on my computer and it is set to executable.  When I double click it a window comes up and asks if I want to 'run in terminal' 'display' 'cancel' 'run'

When I click 'run' it starts up fine and everything is good.  But I want to run this program at startup and I can't figure out a command that works from the terminal. I keep getting this error:

```
gregory@Greg-Lap:~$ sh /home/gregory/Downloads/GmoteServerLinux2.0.0/GmoteServer.sh
Starting GmoteServer 2.0 ... 
GmoteServer started.
gregory@Greg-Lap:~$ Exception in thread "main" java.lang.NoClassDefFoundError: org/gmote/server/GmoteServerUiLinux
Caused by: java.lang.ClassNotFoundException: org.gmote.server.GmoteServerUiLinux
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
Could not find the main class: org.gmote.server.GmoteServerUiLinux. Program will exit.

```

Any advice would be appreciated.  Thank you

---

### Post by Physical Hook on 2009-12-13
```
cd /home/gregory/Downloads/GmoteServerLinux2.0.0 && sh ./GmoteServer.sh

```

Still the same error ?

---

### Post by gschier on 2009-12-13
That worked great! 
Thanks for the help:D

---

