---
title: "Tools package missing from Java?"
date: 2011-01-03
forum: General Help
---

### Post by zerubbabel on 2011-01-03
For some time I've been using the Impose tool in Multivalent.jar to do pdf impositions, but all of a sudden the same script I've always used fails with the message: 

[INDENT]Exception in thread "main" java.lang.NoClassDefFoundError: tool/pdf/Impose
Caused by: java.lang.ClassNotFoundException: tool.pdf.Impose
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: tool.pdf.Impose.  Program will exit.
[/INDENT]
The command that produces this is:

[INDENT]java -classpath ~/Multivalent.jar tool.pdf.Impose -dim 4x2 -layout 16,1,4,13,9u,8u,5u,12u,14,3,2,15,11u,6u,7u,10u -paper "17x11 in" document.pdf
[/INDENT]
"java -version" yields:

[INDENT]java version "1.6.0_21"
Java(TM) SE Runtime Environment (build 1.6.0_21-b06)
Java HotSpot(TM) 64-Bit Server VM (build 17.0-b16, mixed mode)
[/INDENT]

On another forum, someone with this same problem was told that the latest version of Java doesn't include the tools package, but no mention was made of how to remedy that lack. I can't seem to find any mention of a "tools package" on the Oracle website.

Has anyone else run into this problem and a solution?

---

### Post by dingodog on 2011-01-03
Woof Woof!

What multivalent build are you using? in latest

**Multivalent20091027.jar** (2.6 MB)

tools have been removed, so, you need a previous build

you can download here (a multivalent build with tools inside)

**[http://www.ziddu.com/download/1794145/Multivalent.tar.gz.html](http://www.ziddu.com/download/1794145/Multivalent.tar.gz.html)**

---

### Post by zerubbabel on 2011-01-04
Oh, I see, it was not Java but Multivalent that had the tools package missing. That is odd, because I don't remember downloading a new Multivalent version since the last time my script worked. Oh, well. Must be getting senile. Thanks for the link. That worked.

---

