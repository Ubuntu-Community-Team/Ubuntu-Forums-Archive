---
title: "Flash works in Konqueror but not Opera"
date: 2009-07-12
forum: General Help
---

### Post by Zill on 2009-07-12
Kubuntu v9.04 (32-bit)
KDE v4.2.2
Opera v9.64
Flash v10,0,22,87

Clean installation of Kubuntu Jaunty.  Installed kubuntu-restricted-extras and flashplugin-installer.  Java and flash now work correctly with the default Konqueror browser.  Flash plugins located as follows:
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/firefox/plugins/flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

Opera 9.64 downloaded and installed from Opera.com website and runs OK, including java, but flash is not working at all.  Tried plugin paths of /usr/lib/flashplugin-installer and /usr/lib/firefox/plugins but flash remains inoperative although Shockwave Flash 10.0 r22 is listed as a detected plugin in the Opera preferences menu. (Tools, Preferences, Advanced, Content, Plug-in options)

Any ideas please about how to get flash working in Opera.

---

### Post by trailofdead on 2009-07-13
I have the same problem in Ubuntu.

Ubuntu 9.04 32bit
Opera 9.64
Flash 10,0,22,87

Seems that flash uses GTK and Opera uses Qt.  When you run opera from a terminal, you get this output ```
Not GTK2 toolkit (got 0).
```
I havent found a solution yet.  I hear it works in Opera 10 though.  I'm probably going to give it a try because I havent been able to find a solution.

---

### Post by Zill on 2009-07-19
Thank you to all for the helpful advice.

My problem was that I had installed the static version of Opera.  When I installed the shared version as suggested by Rog131 in [this thread]("http://kubuntuforums.net/forums/index.php?topic=3105075.msg188166"), flash worked correctly. :D

So, thanks again for your assistance with this.

---

