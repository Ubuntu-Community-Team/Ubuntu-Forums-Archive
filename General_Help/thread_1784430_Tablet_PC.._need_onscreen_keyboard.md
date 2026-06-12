---
title: "Tablet PC.. need onscreen keyboard"
date: 2011-06-16
forum: General Help
---

### Post by USFMD82 on 2011-06-16
So when I login to xubuntu it allows me to use "on board" but once the desktop is up its nowhere. I have to hook a usb keyboard up to use it. Ive tried accessibility under settings but don't see it in there. How can I make it accessible at all times Ideally an icon up by the clock and my wireless networks.. thanks!

---

### Post by Favux on 2011-06-17
Don't know which release of Ubuntu you are using.  But it should be in Applications > Universal Access > Onboard Settings.  In the General tab check Start onboard minimized.

You might also want to take a look at some of the others such as CellWriter.

---

### Post by USFMD82 on 2011-06-17
using 11.04 I think I tried that before ill try again.

Universal access is not in that path nor is it under the area where settings are. Om board is installed thpugh because when I attach a keyboard and type it in terminal it comes up

---

### Post by Favux on 2011-06-17
That's weird.  You're right, it is installed but doesn't show up in the Applications finder.  CellWriter and Florence do show up interestingly enough.  That's a bug I think.  You might want to file it on Launchpad.

In a terminal enter *onboard-settings* or right click on the Desktop and chose create Launcher.  In the Command box enter */usr/bin/onboard*.

---

