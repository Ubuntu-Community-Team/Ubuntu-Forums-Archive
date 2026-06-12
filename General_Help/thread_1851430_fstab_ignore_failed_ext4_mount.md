---
title: "fstab ignore failed ext4 mount"
date: 2011-09-28
forum: General Help
---

### Post by yettey on 2011-09-28
Hello,

I have looked around and can't figure out which options to use in /etc/fstab to ignore a failed mount. This is on Ubuntu 11.04. 

My current settings are 
...
/dev/sdb   /data   ext4   defaults   0   0
...

I want to put something in like
...
/dev/sdb   /data   ext4   defaults[if fails, ignore]   0   0
/dev/sdc   /data   ext4   defaults[if fails, ignore]   0   0
...

The reason for this is I am using a PCI Sata controller and for some unknown reason the sdb/sdc changes randomly on reboot. The main hd is a scsi raid of 2 disks. (Dell Poweredge 2850 server). If you don't know how to do the ignore on fail, do you know how to force the same sdb/sdc assignment?

Thanks!

---

### Post by dino99 on 2011-09-28
here is my fstab:

proc /proc proc defaults 0 2
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523 /home ext3 defaults,relatime 0 2
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16 none swap sw 0 0

as you can see its a minimal config: only /home & swap partitions. They use uuid so no permutation as yours possible.

Do yours like that, there is no need for more complicated, everything else is done by mountall package. (sudo gedit /etc/fstab)

How to get uuid: sudo blkid

and update these:
sudo update-usbids && sudo update-pciids

---

