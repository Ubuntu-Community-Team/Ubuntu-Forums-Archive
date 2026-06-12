---
title: "firefox can't open file using dolphin...."
date: 2009-11-30
forum: General Help
---

### Post by muctadir on 2009-11-30
firefox is unable to open file using dolphin. if i right click on downloaded file of the download window, it asks for something to choose. besides, if i want to save file in a location, the file browser takes too much time to open.....

---

### Post by Zorael on 2009-11-30
You could point to Dolphin when it asks for it; it's at **/usr/bin/dolphin**.

There's also work on [better Firefox integration in KDE](http://en.opensuse.org/KDE/FirefoxIntegration), but it's not in the official repos. [Felix Geyer](https://launchpad.net/~debfx) has [a PPA](https://launchpad.net/~debfx/+archive/firefox-kde) that contains packages of it.

Your package manager of choice should recognize an update to Firefox after having added it. You may also need to manually select and install **kmozillahelper**.

After doing this, hopefully it will be more aware of what apps KDE use (Dolphin), and it should use KDE's file open/save/etc dialog windows.

---

### Post by muctadir on 2009-12-03
thank you very much

---

### Post by mo.mashi on 2011-01-19
Another way of doing it would be to download: kmozillahelper . It not only sends you to dolphin out of Firefox but when the open or save dialog come up, you get the Native KDE one which is uber cooler then the Firefox Linux one...

[edit] hahaha, I just read the second part of your reply, you were recommending kmozillahelper as well... oops.

> **Zorael said:**
> You could point to Dolphin when it asks for it; it's at **/usr/bin/dolphin**.

There's also work on [better Firefox integration in KDE]("http://en.opensuse.org/KDE/FirefoxIntegration"), but it's not in the official repos. [Felix Geyer]("https://launchpad.net/%7Edebfx") has [a PPA]("https://launchpad.net/%7Edebfx/+archive/firefox-kde") that contains packages of it.

Your package manager of choice should recognize an update to Firefox after having added it. You may also need to manually select and install **kmozillahelper**.

After doing this, hopefully it will be more aware of what apps KDE use (Dolphin), and it should use KDE's file open/save/etc dialog windows.

---

### Post by SeijiSensei on 2011-01-19
What a great application!  Thanks for pointing out kmozillahelper.  I was always annoyed that I couldn't bring up a KDE file dialog in Firefox.  Now I can!

---

