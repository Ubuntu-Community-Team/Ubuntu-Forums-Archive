---
title: "Downgrade GDM to 2.20 in Ubuntu 10.04 Lucid"
date: 2010-09-09
forum: General Help
---

### Post by talvik on 2010-09-09
**The result**
After following these instructions you'll get:
-GDM 2.20, with all the features(themes, feature complete, configurable...)
-No Plymouth, or any graphical boot (haven't found a way to run old gdm along with Plymouth)

**Instructions**
These instructions are based on this post [http://ubuntuforums.org/showthread.php?p=8350408](http://ubuntuforums.org/showthread.php?p=8350408) but they won't work on Lucid 10.04

[LIST=1]
[*]Download GDM 2.20 on this [link]("http://packages.ubuntu.com/karmic/i386/gdm-2.20/download").
[*]Remove gdm and install the downloaded package.
```
sudo apt-get remove gdm
sudo dpkg -i gdm*.deb
sudo mv /etc/init/gdm.conf /etc/init/gdm.bak
```
[*]Run these commands (related to a bug in this package):
```
cd /usr
sudo mkdir X11R6
cd X11R6
sudo ln -s /usr/bin bin
```
[*]Disable the graphical boot (reason: Plymouth loads X, and old gdm can't connect, fixes are welcome)
-Edit /etc/default/grub and change
```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```
[*]Run: ```
sudo update-grub2
```
[*]Reboot and hope for the best
[/LIST]

ps: Most posts asking about how to get old GDM back get dismissed, because most people think the only motivation is visual. A lot of posts got buried cause' of this.

---

### Post by doctorzeus on 2010-11-04
So am I to understand this will allow all the Login sceen customisation options of versions <= 8.04 Hardy on 10.05 Lucid!?:)

That would be awesome!!

Ill try it now!!

---

### Post by doctorzeus on 2010-11-05
Thanks so much! It worked!

Only thing is I had to move "/etc/init/gdm.conf" to "/etc/init/gdm.bak" otherwise there would be a conflict on startup...

Thanks

Doctorzeus

---

### Post by talvik on 2010-11-17
Thanks for the addition.

Have you had any luck keeping the graphical boot?

---

