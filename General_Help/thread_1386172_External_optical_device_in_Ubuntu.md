---
title: "External optical device in Ubuntu?"
date: 2010-01-20
forum: General Help
---

### Post by Pipps on 2010-01-20
I have a SATA desktop hard drive. It is currently sat inside my desktop machine and powered by it.

I have connected the the SATA connection to a USB adapter:

[img]http://www.pinkytwist.co.uk/pinky/UK/CA055/CA055_g1.jpg[/img]

I have connected the USB adapter to my Dell Mini 10 Netbook.

When I boot-up into Ubuntu, I cannot see the connected CD-ROM device anywhere. It also does not appear when I type 'fdisk -l' in the terminal.

How can I access this external optical device in Ubuntu?

---

### Post by synapsys on 2010-01-20
nvm

---

### Post by Pipps on 2010-01-20
I can confirm that even when I eject and re-enter the CD in the Sata drive, it spins up nicely, but nothing happens in Ubuntu.

How can I mount this CD-ROM?

---

### Post by synapsys on 2010-01-20
Quick thought, have you tried rebooting the netbook whilst having the cdrom drive plugged in? Maybe see if it is recognized that way under /media/cdrom0

---

### Post by Pipps on 2010-01-20
I have tried rebooting with the CD-ROM connected, exactly as you suggest, but the device is still not visible in either /media or /mnt.

What should I do in order to access this optical device in Ubuntu?

---

### Post by ajgreeny on 2010-01-20
Have a look in /etc/fstab where there should be a line something like this:-
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
If this is not present, you will need to edit the file to include such a line.  If you only have a single disk in the machine the cdrom may not be sdc in your case, but sdb.  I have 2 disks hence my sdc for cdrom.

---

### Post by Pipps on 2010-01-22
Thank you, everyone. Your combined support really helped me! :)

---

