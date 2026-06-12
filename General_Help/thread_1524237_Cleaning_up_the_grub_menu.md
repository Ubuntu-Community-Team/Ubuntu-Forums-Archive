---
title: "Cleaning up the grub menu"
date: 2010-07-04
forum: General Help
---

### Post by xtheunknown0 on 2010-07-04
I see too many entries upon turning on my laptop: [http://sites.google.com/site/xtheunknown0/boot-info-script](http://sites.google.com/site/xtheunknown0/boot-info-script)

There should only be 3 entries: Windows partition, Ubuntu partition, and the memtest thing, I believe.

The *doubling* up of Windows and Ubuntu is due to me wiping Ubuntu, then reinstalling Ubuntu.

The third entry for Ubuntu is due to re apt-get install'ing gnome-desktop.

How can simplify the menu?

---

### Post by oldfred on 2010-07-04
Grub shows each kernel and does not delete old kernels when a new is downloaded. You have three kernels shown, it is best to keep one older one just in case there are issues with the newest. Kernels do not take a lot of room on hard drive, so unless you need every bit of space you only have to houseclean occasionaly. You show a recovery partition and grub sees it as another windows so it lists that also.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

Houseclean old kernels:
Do not delete the kernel you are using, this shows current version:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

