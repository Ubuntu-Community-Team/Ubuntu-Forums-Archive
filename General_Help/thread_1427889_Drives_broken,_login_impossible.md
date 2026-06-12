---
title: "Drives broken, login impossible"
date: 2010-03-12
forum: General Help
---

### Post by flim on 2010-03-12
Hi there,

I've had a strange computer failure due to a broken usb port - and that caused all 5 partitions to go bananas. I've fixed them using fsck etc, and the computer now boots again. However, it looks like the shadow/passwd file got broken in the process - graphical login just comes up with a popup saying authorization error before I can even type something and console displays a similar error repeatedly (again, without me typing anything).

I booted from install cd and tried to access the drive in question from there. However, while fdisk -l shows all drives/partitions, they are not listed in /dev.

fdisk -l would e.g. show
/dev/sda1  *   1 12158  97659103+  83 Linux

but ll /dev/sda* just shows /dev/sda, no partitions at all. Other drives are listed, but when trying to mount them, I get "mount: /dev/sdb2 already mounted or drive2/ busy". The partition isn't mounted, and I've no clue how the newly created directory could be "busy" (tested that, location doesn't seem to matter)

I've got no clue how to mount the drive to fix anything with it not being listed in /dev... and I'm wondering how the system itself can boot up from /dev/sda1 till login prompt, when the cd can't even see the partitions?

Any help/hints would be greatly appreciated!

cheers
flim

---

### Post by DawieS on 2010-03-12
I would recommend a clean install from the live CD, after updating your backups.

In the past, I have found that it is too time-consuming trying to repair an installation caused by hardware failure. As soon as you repair the first hurdle, the next one shows up, and you never know how many still lie ahead.

I have created my own personal repository from installed applications and downloaded updates. I have also taken notes on my customizing preferences, saved in a text file, that are backed up along with the repository and my personal data. A clean install, fully updated and customized with applications installed, now takes less than 2 hours.

An added advantage is that you will also get rid of unwanted "leftovers" from previously de-installed applications.:razz:

---

