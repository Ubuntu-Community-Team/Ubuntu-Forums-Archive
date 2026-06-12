---
title: "Mounting CD"
date: 2010-09-17
forum: General Help
---

### Post by jokes_finder on 2010-09-17
Hello,

I connected the CD ROM to the board VIA (USB 2.0 to SATA/IDE cable)
But Ubuntu 10.04 didn't mount it automatically

so I typed the command:
wodim --devices

to detect CD ROM device

the output was:
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'SONY' 'CD-RW  CRX220E1'
-------------------------------------------------------------------------

and I know that my Kernel supports iso9660 ( using the command "cat /proc/filesystems" )

so, to mount the CD device I typed:
sudo mount -t iso9660 /dev/scd0 /media/cdrom0/

And the output was:
mount: no medium found on /dev/sr0

And I typed the command:
sudo mount -t iso9660 /dev/sr0 /media/cdrom0/

and also the same output:
mount: no medium found on /dev/sr0

Any help?

---

### Post by jokes_finder on 2010-09-18
No help?

---

