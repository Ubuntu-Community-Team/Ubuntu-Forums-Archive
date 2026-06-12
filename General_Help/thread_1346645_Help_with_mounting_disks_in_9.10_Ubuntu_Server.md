---
title: "Help with mounting disks in 9.10 Ubuntu Server"
date: 2009-12-05
forum: General Help
---

### Post by cybesystem on 2009-12-05
Hello!

I'm kind of new to Ubuntu, so please be gentle if I've done some simple mistake.

Scenario:
I installed the latest ubuntu server I could find, 9.10 i reckon.
I installed VNC and set up SSH.
The PC got 3 disks, one is the system disk. I wish to mount the 2 other, and share them via the network.

Problem is, the xfce desktop handler wont show them to me, as KDE have done on other machines for me, so I went down into /media/ and found nothing as well. Now I have no idea where to look, nor what to do, in order to mount the disks.

So my question is, how do I mount all available disks - and if possible, how to do this on startup?

Thanks in advance!

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
If you're not familiar with the command line I guess now is the time to get there. The command ```
man mount
``` will show you a manual page for the mount command and give you everything that command is capable of. ```
mount -a
``` will mount everything but this can be problematic. To see your disks you need to list them. you can do so with fdisk. ```
man fdisk
``` is obviously the fdisk manual. I believe you are looking for ```
fdisk -l
``` to list all of your partitions. If the disk or partition you want to mount is at /dev/sda1 then you would use ```
sudo mkdir /media/disk1
sudo mount /dev/sda1 /media/disk1
``` This isn't necessarily exactly what you HAVE to type. You can change /media/disk1 to anything... like /home/user/gwantanimo or /etc/mydisk but the /dev/sda1 is what it is. You can set all these to mount automatically in fstab. You can learn how to edit the fstab using ```
man fstab
```. Or you can use a gui app called pysdm but you will more than likely need to manually change some things in the fstab regardless. From then on you will always have them in the window manager.

---

### Post by cybesystem on 2009-12-05
Thank you! Will be reading the manual pages and figure out how to automount!

Most important was just to be able to do it for now. Thanks.

---

