---
title: "Azureus not loading after using auto-update"
date: 2006-03-23
forum: General Help
---

### Post by speanort on 2006-03-23
I recently installed Azureus onto Ubuntu 5.10 and it was working, but the auto-update program for Azureus came up to update the program. I thought this would be fine to do. It ended up having multiple downloads and had to restart about 3-4 times to install all the updates. After the last one was installed I had to restart it and now Azureus does not come up at all.

This is the output in Terminal when I try to start Azureus:

```
speanort@ubuntu:~$ azureus
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
```

Does anyone have any ideas as to what I can do to solve my problem. I have tried multiple things, such as reinstalling Azureus, reinstalling Java and changing what Ubuntu points to to use Java. None of these have solved the problem. :-k I still can't load Azureus.  I would appreciate any input.

---

### Post by just1pepsi on 2006-03-23
I too am needed help with this. 

What I have done several times now, is remove it and the .azureus folder in my home directory and reinstall it. This corrects it until it downloads the gtk update, then it throws this error.

I've searched all over and cannot find anything useful to fix this issue once and for all.

---

### Post by speanort on 2006-03-23
I didn't even think about removing the .azureus folder. You are right. There has to be a fix for this problem. I can't see this problem only happening to us, someone has to know a solution. Thanks for the reply though.

---

### Post by anodizer on 2006-03-23
I don't know if there is a solution to this problem, but I think it's better to remove the Azureus version installed from the repos and download the latest source from the official site. Extract it somewhere, let's say /opt/azureus and run it with: /opt/azureus/azureus. It's working and upgrading properly this way and you do not lose your config (you must not delete the .azureus folder in your home directory to keep your settigns).
Hope that helps.

---

### Post by Barrakketh on 2006-03-23
Agreed.  I personally created a directory named "bin" in my home folder and untarred the package there.  The Azureus in the repositories are an old version anyway (even in Dapper!), so you get the latest and greatest :)

---

### Post by just1pepsi on 2006-03-29
Thanks for the tip, now it works great!

---

