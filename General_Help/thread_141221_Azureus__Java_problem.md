---
title: "Azureus / Java problem"
date: 2006-03-07
forum: General Help
---

### Post by Sherlock Holmboy on 2006-03-07
im having a problem getting azureus to start. when launched in the terminal i get the following error:
```

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
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:109)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:158)

```
can somebody tell me what this means?
i had it working properly before, but one day it just seemed to quit working. :cry:

---

### Post by rm -rf *.* on 2006-03-07
Is the correct java installation selected?

```
sudo update-alternatives --config java
```

---

### Post by Style on 2006-03-07
I have the correct java installed and selected, and I have the same problem. it happened after an update for the graphical interface of azureus.

---

### Post by Sherlock Holmboy on 2006-03-08
[QUOTE=Style]it happened after an update for the graphical interface of azureus.[/QUOTE]
i forgot to mention that i did the update right before it quit

---

### Post by rm -rf *.* on 2006-03-08
What about when you launch other java applications?? I would try to isolate the problem either to your java installation/environment or azureus.

---

### Post by akiro.yamamoto on 2006-03-08
Edit for content and relevance....... My bad! :oops: #-o

---

### Post by Sherlock Holmboy on 2006-03-10
my frostwire is working fine

---

### Post by Mr Green on 2006-03-10
Edit your azureus startup script to point to the correct swt library or something like that.

---

### Post by Baris on 2006-03-11
This is not a java problem per se, its a problem with the intermediate graphical toolkit being used.  I realise this isn't particularly helpful, but before you go screwing up something that does work, like your current java installation, I thought it best to mention.  I too have this problem.

---

### Post by Sherlock Holmboy on 2006-03-11
all my other java stuff is working fine, but i don't really understand what to do with the previous two posts :-k

---

### Post by rm -rf *.* on 2006-03-11
Have you posted this error on the [Azureus forum]("http://sourceforge.net/forum/forum.php?forum_id=349817") yet? I would think they would be your best bet since it doesn't seem to be a problem with Ubuntu or your Java installation.

---

### Post by dpaint4 on 2006-03-11
Ha! I *just* jumped through the hoops of installing Azureus for the first time, and it worked exactly long enough to download the updates and break itself. So I ditched it for the time being. Funny though.

Yeah. It's broken. I watched it do it to itself.

---

### Post by Sherlock Holmboy on 2006-03-13
i downloaded and extracted the latest build and it works so i guess it was just a bug in that version that automatix installed

edit:

here's the [link]("http://torrents.aelitis.com:88/files/Azureus_2.4.0.2RC_linux.tar.bz2") to the tarball

---

### Post by jonas.p on 2006-03-14
you can edit your azureus start script /usr/bin/azureus

change
```
-Djava.library.path=/usr/lib/jni:/usr/lib
```
to
```
-Djava.library.path=/usr/lib/jni:/usr/lib:.
```
since the needed library is in $HOME/.azureus/

worked fine for me

---

### Post by GreveFelix on 2006-03-14
Hey I am very new to Umbutu and Linux aswell! But I use "bittornado" instead of azureus! I think it is even better and no JAVA is requiered ...

---

