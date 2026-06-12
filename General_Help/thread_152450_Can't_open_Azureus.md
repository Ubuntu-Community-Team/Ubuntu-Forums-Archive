---
title: "Can't open Azureus"
date: 2006-03-29
forum: General Help
---

### Post by zorkerz on 2006-03-29
Hello I reciently realized that my azureus will not open well i tell it to run.  When run in a terminal i get this.
zorkerz@Estle:~$ azureus
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

It looks like something is wrong with java?  I really have no idea what else to do.  I've uninstalled and reinstalled both jave and azureus without any change.  Any ideas let me know.  Thanx
elias

---

### Post by nanotube on 2006-03-30
have a read of this:
[http://azureus.sourceforge.net/faq.php#1](http://azureus.sourceforge.net/faq.php#1)

---

