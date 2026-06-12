---
title: "saving settings"
date: 2009-10-28
forum: General Help
---

### Post by jesuisbenjamin on 2009-10-28
Hello everyone,

i would like to save as much of my personal setting before i re-install/upgrade Ubuntu. It would be best if i could avoid the hassle of re-creating my desktop environment from scratches, so i would like to save as much as i can before re-installation/upgrade.

**Gnome Panel:** Since my current panel settings are re-loaded at boot, i assume there is an a file holding the necessary information (on transparency, launchers, position etc.)
Where can i find this file and can i paste this file after re-installation/upgrade to retrieve my current settings?

---

### Post by P4man on 2009-10-28
If you do an upgrade using update-manager, all your settings will be preserved. there are other ways, but thats probably the easiest.

---

### Post by jesuisbenjamin on 2009-10-28
I currently have a dual-boot with Vista which i would like to remove from my HD.

I'd like to know the alternative.

---

### Post by P4man on 2009-10-28
I think if you backup all the hidden .folders in your home (like 
.gnome .gnome2 .config .compiz,..) and restore them later you should be mostly okay.

---

### Post by jesuisbenjamin on 2009-10-28
It seems like you are doubting (?)

---

### Post by P4man on 2009-10-28
Yep. First of all, my name is not Linus Torvarlds and I have never tried it myself. Secondly im not sure if the havent changed the place where does settings are saved between  8.10 (or what are you upgrading from?) and 9.04 or 9.10

Im assuming but not betting my life on it.

---

### Post by QLee on 2009-10-28
Everything to do with userspace settings (on default install) is contained in the user's home folder. (except if someone has installed something other than with the package manager and put the software and configuration files somewhere else, symlinked to it or something).

So as P4man told you, the settings you're asking about are in your /home. 

As also suggested, there are sensible upgrade paths from a previous install version. I wouldn't recommend trying to upgrade from anything except the previous version number.

Lots of people choose to backup their home folder and then to restore it to a fresh install in order to try and retain their settings, this mostly works, except in the case major revisions where the format of a configuration file has changed for a particular piece of software and that is pretty rare but I suspect that's the cause for P4man to qualify the statement made.

---

### Post by jesuisbenjamin on 2009-10-28
Thanks for clearing up guys!

---

