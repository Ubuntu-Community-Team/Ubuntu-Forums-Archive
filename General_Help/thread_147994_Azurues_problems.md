---
title: "Azurues problems"
date: 2006-03-21
forum: General Help
---

### Post by AxelW on 2006-03-21
Hi, just recently changed from windows to ubuntu. 

Everything has gone smoothly until now, when I try to start azuerus i get the following error:

Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in java.library.path
at java.lang.ClassLoader.loadLibrary(Unknown Source)
at java.lang.Runtime.loadLibrary0(Unknown Source)
at java.lang.System.loadLibrary(Unknown Source)
at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
axel@ubuntu:~$

---

### Post by steve.horsley on 2006-03-21
Have you installed Sun's JVM? I'm not sure, but I think this may be a problem with the default Blackdown JVM

---

### Post by Perfect Storm on 2006-03-21
You might check this: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

---

### Post by AxelW on 2006-03-21
The problem is that i cannot remove azureus, when i try to delete the folder i get a message saying i don't have permission and "add application" can't find azureus

---

### Post by Perfect Storm on 2006-03-21
How did you install it? and where did you install it?

---

### Post by AxelW on 2006-03-21
/usr/lib/

and i followed this guide:

[http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/](http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/)

thanks for all the help.

---

### Post by Nasso on 2006-03-22
i have the same problem. my azureus worked before but it suddenly stopped working :P

---

