---
title: "Kubuntu won't Show Desktop Right"
date: 2011-05-23
forum: General Help
---

### Post by mttrackmaster38 on 2011-05-23
I tried installing Kubuntu 10.10 yesterday and when I booted into the desktop it wouldn't show anything but blurriness and lines. It was completely unusable. It showed that on the live cd too. I then tried install Elementary OS. It installed and had the same result. This is getting extremely frustrating and I have no idea of what to do. I forgot to take a screenshot of either one but I found one on the elementary launchpad bug page. Oh yeah, this happened when I tried to install the alpha of Ubuntu 11.04 too. please help.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Does this happen with 9.04?

---

### Post by mttrackmaster38 on 2011-05-23
Nope. It never did that when I installed that version. That was the version I started Ubuntu with.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Can you do me a favor and post the results in terminal of:[FONT=monospace][B]

hwinfo --short[/B][/FONT]

---

### Post by Wolfenberg on 2011-05-23
This image appears on first boot when not working video card drivers. Try to reboot and install them. You may have to change the kernel in the system at a new one.

---

### Post by mttrackmaster38 on 2011-05-23
@linuxinstalledfromhdd- I have no idea how I would get you the log file. @wolfenberg- I can only get into the recovery mode terminal but I have no idea how to connect to a wireless network. My laptop wireless is working it just isnt connected to anything.

---

### Post by linuxinstalledfromhdd on 2011-05-23
If you can't pull up the log files or specs for me, the best bet at this point would be to reinstall Ubuntu again.  Don't delete the original partition, let the installer resize your partition for you. That way your data will hopefully still be there.  Here is a nice walkthrough once you get it installed:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Try using 10.10 too.

---

