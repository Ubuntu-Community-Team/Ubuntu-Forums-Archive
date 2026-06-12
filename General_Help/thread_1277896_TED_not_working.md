---
title: "TED not working"
date: 2009-09-28
forum: General Help
---

### Post by Quiksilvermp3 on 2009-09-28
Hello,
I am having trouble with TED (torrent episode downloader).  I was able to run through the set up wizard but after that nothing.
Here is what is displayed in terminal:
Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1698)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.<clinit>(Unknown Source)
    at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
    at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
    at org.jdesktop.jdic.tray.SystemTray.<clinit>(Unknown Source)
    at ted.TedTrayIcon.<init>(TedTrayIcon.java:28)
    at ted.TedMainDialog.initGUI(TedMainDialog.java:312)
    at ted.TedMainDialog.<init>(TedMainDialog.java:121)
    at ted.TedMain.main(TedMain.java:37)

---

### Post by FuePi on 2011-05-13
Just had the same problem after upgrading ted from version 0.9715 to 0.972.

I found this HOWTO: 
[http://wlmtips.com/2010/02/04/how-to-install-ted-torrent-episode-downloader-in-linux/](http://wlmtips.com/2010/02/04/how-to-install-ted-torrent-episode-downloader-in-linux/)

The trick is to use the option **noTray** when starting ted:
```
java -jar ted.jar noTray
```

That solved the problem :)

---

