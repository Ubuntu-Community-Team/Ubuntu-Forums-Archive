---
title: "Internal drives suddenly not mounting (only boot drive mounts)..."
date: 2012-08-26
forum: General Help
---

### Post by killabee44 on 2012-08-26
Guys,

I am having a problem where my internal drives (other than the partitions on my boot drive) are not mounting.

This is something new. They used to mount fine. I have a feeling that it might have something to do with one of the last updates. 

The drives are detected by the bios and by ubuntu, they are just not mounting. 

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=177d552f-a53d-4410-b997-976d4d5f9216 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=fbef488f-ccd0-4b81-9ca2-5d469bdf16ab /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=02c7a2a4-97de-4c3d-b8c2-1288a9b14de2 none            swap    sw              0       0
```


Here is: sudo blkid -c /dev/null:

```
/dev/sda1: UUID="177d552f-a53d-4410-b997-976d4d5f9216" TYPE="ext4" 
/dev/sda2: UUID="fbef488f-ccd0-4b81-9ca2-5d469bdf16ab" TYPE="ext4" 
/dev/sda3: UUID="02c7a2a4-97de-4c3d-b8c2-1288a9b14de2" TYPE="swap" 
/dev/sda4: UUID="d951b9b5-a78f-4363-b812-25927e8e8412" TYPE="ext4" 
/dev/sdb1: LABEL="2tbCaviar" UUID="1626c7f8-7979-4068-b182-829ef8d42bb9" TYPE="ext4" 
/dev/sdc1: LABEL="250Backup" UUID="B420A64C20A61600" TYPE="ntfs" 
/dev/sdd1: LABEL="250Newsleecher" UUID="70B4D348B4D31008" TYPE="ntfs" 
/dev/zram0: UUID="41914a49-534f-470e-86f0-f5bec829a98d" TYPE="swap"
``` 

If anyone can shed some light to this issue, I would appreciate it.. Thanks.

---

### Post by killabee44 on 2012-08-28
btw.. 

The only thing in my media folder is CDrom.

---

### Post by oldfred on 2012-08-28
Your fstab only has / (root), /home & swap. None of your data partitions are in fstab. If mounted with Nautilus, unmount before updating fstab.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by killabee44 on 2012-08-29
Thanks Fred, Ill take a look at those links.

---

### Post by killabee44 on 2012-08-31
Oldfred, or anyone else that might reply.. I can't even see the drives on the left side in Nautilus when they are not mounted. I used to be able to see them there. 

So, is anyone else experiencing this?

---

### Post by oldfred on 2012-08-31
Where are you mounting them. If not mounted they should show.

If mounted with fstab into /home or /media they may show twice the second will not work and has an underscore at the end. I typically mount in /mnt just so partitions I automatically mount do not appear in Nautilus.

I also label all the partitions so I know what they are. I use gparted or Disk Utility to update labels.

---

### Post by killabee44 on 2012-08-31
oldfred,

They are not mounted and still do not show up on the left side of Nautilus at all. I have several partitions labeled already. 

Three of the labels are:

2tbCaviar

250Backup

250Newsleecher

---

### Post by oldfred on 2012-08-31
Does the sudo blkid still show them? If you go to Computer in Nautilus does it show them in both panes?  The ones in the right for me show drive, label and everything else is unknown? But they are in both panels.

---

### Post by killabee44 on 2012-08-31
oldfred,

After some updates and another reboot, the problem seems to be gone. Something going on with my system. Hopefully I won't see this again. 

Ill work with the links you gave me so that those partitions auto mount at boot. 

Thanks.

---

