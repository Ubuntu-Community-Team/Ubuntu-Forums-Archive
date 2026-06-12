---
title: "Can't see my second Hard Drive"
date: 2010-06-08
forum: General Help
---

### Post by Narpstar on 2010-06-08
Hi guys,

I've VERY new to Ubuntu, so just learning how everything works, but I've come across a problem where I can't access (or even see) my second hard drive in my computer.

I don't know whether or not Ubuntu can see it at all, as I don't know what command to type into Terminal to check - but it's definitely not available in the Places folder.

I used to be able to see and access the second hard drive, but I'm pretty sure it was when I performed an automatic update that it stopped appearing.

Any ideas?

Cheers guys,
Ben

---

### Post by darkdragn on 2010-06-08
To see if your computer is even seeing the hdd, go to the terminal and type 

fdisk -l

If it is indeed your second HDD, it should be something along the lines of /dev/sdb. If it's the first partition you want to mount, create a folder in either /mnt or /media, and mount it:

cd /media
mkdir temp
mount /dev/sdb1 /media/temp

---

### Post by Narpstar on 2010-06-09
Hey thanks, you were right! It just needed to be mounted. Now how do I ensure it is automounted every time I boot up? Or is it possible to map the drive or something? When it was automounting before, it would take a fair while to load the drive. Unlike Wondows, which seemed instantaneous.

Cheers,
ben

---

### Post by garvinrick4 on 2010-06-09
If it is a USB drive then install "gconf-editor"

sudo apt-get install gconf-editor

Go to Applications/ Configuration Editor to Apps to Nautilus to Preferences and make sure that the box is checked for automount. It should always show up in Places if it is plugged in when you boot up. And if you plug it in after boot should only take a few seconds to mount.

---

### Post by darkdragn on 2010-06-09
For it to be loaded automatically, i would modify your fstab. 
(If you have vim installed... if not use vi or nano)
vim /etc/fstab

It should look something like this


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=91302ad0-351b-4c28-b75f-d81c342910a4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9bfecb95-9118-405d-80ef-31139ae4c949 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


If those were the right options, then if you wanted to you could just insert this line after the last line in the file.

/dev/sdb1        /media/Win        ntfs-3g        defaults        0        0

Just make sure that the folder /media/Win exists. It should show up in the left hand side of nautilus after your next boot... or if you're impatient you could make sure it isn't already mounted and tell mount to hit everything in fstab.

mkdir /media/Win
umount /dev/sdb1
mount -a

Then close nautilus, and reopen it, check if it's there... but either way, if you navigate to /media/Win it will all be there, ^_^.

---

### Post by Narpstar on 2010-06-12
Hmmm... I'm almost following you.

Yes, fstab DID look like that... 


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=65c4220b-a1d5-4a81-8ed2-ee1efe10d7e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=82ec9a37-34c4-42b1-a555-43f055d61da1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Not EXACTLY as you wrote it though... so I'm not sure what to modify, nor how to modify it. I don't know what the vast majority of it all means.

Thanks!
Ben

---

### Post by Narpstar on 2010-06-12
Oh and btw, /media/win/ doesn't exist on my machine.

---

### Post by dino99 on 2010-06-12
choose the easiest way: install mountmanager (with synaptic) and set your preferences with it (system admin mountmanager)

---

### Post by Narpstar on 2010-06-14
> **dino99 said:**
> choose the easiest way: install mountmanager (with synaptic) and set your preferences with it (system admin mountmanager)

That's what I'M talkin about - graphical solutions. Thanks Dino!!

---

### Post by daenas on 2010-06-19
This is what I've been looking for as well!  Some of us are so new that fstab scares us and we really aren't sure what to do, even with instructions.  I've been looking for an answer like this for a looong time!  Thanks!  ;)

---

### Post by Morbius1 on 2010-06-19
It's funny and I guess it's just me but I've always added expressions in fstab directly using these as templates :

> /dev/sda1 /media/WinC ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
/dev/sda6 /media/WinD vfat utf8,umask=007,uid=1000,gid=46 0 2
/dev/sdb6 /media/Data ext3 defaults,noatime 0 2
I may adjust the options depending on my needs but for the most part this is what I use.

Mountmanager, on the other hand, scares me ( see attachment ) :wink:

---

