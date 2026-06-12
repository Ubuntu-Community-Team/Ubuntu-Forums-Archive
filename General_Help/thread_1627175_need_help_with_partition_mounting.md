---
title: "need help with partition mounting"
date: 2010-11-21
forum: General Help
---

### Post by houcem on 2010-11-21
I have three main partitions on a SATA 160GB HDD a 60GB partition labeled WinVista, a 30GB one labeled WinXP and a 40GB one labeled Storage to store my files.

I've recently installed Ubuntu 10.04 on a forth main partition and during the installation I've chosen to mount Vista to media/WinVista and WinXP to media/WinXP but I've mounted Storage to /mnt without a sub-folder.
As a result I can see both WinVista and WinXP partitions  on the Places menu and they are mounted only when I click on it, besides they are shown on the desktop which is very good but the Storage partition is always mounted to mnt/ and it isn't visible anywhere.

So please can you help modifying that so I can permanently mount Storage to media/Storage like the others.

I've tried manually unmounting Storage from mnt/ and mounting it to media/Storage but it is not permanent, I mean everything is gone when I restart my computer.

---

### Post by DeMus on 2010-11-21
How did you mount your partitions? Did you do that in /etc/fstab?
If so, could you send the complete listing of that file please?
If you did it in another way please also post the exact way of how you did it.

---

### Post by houcem on 2010-11-21
I did it during the installation in front of each partition the wizard lets you choose a mount point.

---

### Post by DeMus on 2010-11-21
> **houcem said:**
> I did it during the installation in front of each partition the wizard lets you choose a mount point.

Okay, but then it must been written in /etc/fstab. Could you please write (copy/paste) the contents of that file so we can have a look.

---

### Post by houcem on 2010-11-21
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=03bfa189-86d0-4062-a925-dacf93baeb56 /               ext4    errors=remount-ro 0       1
# /mnt was on /dev/sda3 during installation
UUID=506EF1D6631257CE /mnt            ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=f2bde891-82e5-4704-b931-a759860021e2 none            swap    sw              0       0

---

### Post by DeMus on 2010-11-21
Please try this:

sudo mkdir /media/Storage
sudo gedit /etc/fstab
[LIST=1]
[*]Go to this line "UUID=506EF1D6631257CE [COLOR="Blue"]/mnt[/COLOR] ntfs defaults,nls=utf8,umask=007,gid=46 0 0"
[*]Change the line into: UUID=506EF1D6631257CE [COLOR="Red"]/media/Storage[/COLOR] ntfs defaults,nls=utf8,umask=007,gid=46 0 0
[*]Save the file and reboot.
[/LIST]

---

### Post by houcem on 2010-11-21
Thx for your precious help

---

### Post by DeMus on 2010-11-21
> **houcem said:**
> Thx for your precious help

It worked as I wrote? That's good to hear. Now please go to the line just above the first post, and click on thread tools. Now choose "mark as solved", if I remember it well.
Have fun with Ubuntu.

---

