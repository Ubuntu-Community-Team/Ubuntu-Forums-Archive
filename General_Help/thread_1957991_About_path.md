---
title: "About path"
date: 2012-04-13
forum: General Help
---

### Post by lolleepop on 2012-04-13
Program fails to work from path.

Hello. I can run a program from folder, and I have put this in my path, and indeed I can call the program. However, this is what happens:

```

me@CrapBook:~$ runXProtTest
Exception in thread "main" java.lang.NoClassDefFoundError: prottest/XProtTest
Caused by: java.lang.ClassNotFoundException: prottest.XProtTest
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
Could not find the main class: prottest.XProtTest.  Program will exit.
me@CrapBook:~$ 

```

Anyone have any insight why like this? As I pointed out, the program runs just fine if I call it from its folder.

---

### Post by abyrne on 2012-04-13
Does the program you're running call on any external resources that were in the original folder but not in the path?

---

### Post by lolleepop on 2012-04-13
Actually, I solved the issue already. The program calls for a jar file, and changing its classpath to absolute within the program worked. Yay :KS

---

### Post by abyrne on 2012-04-13
> Actually, I solved the issue already. The program calls for a jar file, and changing its classpath to absolute within the program worked. Yay 
Yup, absolute paths almost always work better than relative ones. Glad you got it fixed!

---

