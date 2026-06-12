---
title: "Cannot mount IDE/usb ntfs hdd"
date: 2009-11-17
forum: General Help
---

### Post by rowbird on 2009-11-17
Hi I have an internal XP drive on an external usb adapter that I cannot mount. It shows up under "Computer" in the menu, but says "unable to mount location, can't mount file. Below are lsusb, dmesg | tail, and fdisk -l images. I would appreciate any help, as I am stumped. Thanks.

---

### Post by rowbird on 2009-11-18
I have got dmesg to recognize the XP drive as sdb on another ubuntu 9.01 machine, although it still does not show up in fdisk -l using the same USB adapter. Below is the output of dmesg on that system.

---

### Post by JBAlaska on 2009-11-18
Have you installed ntfs-3g
```
sudo apt-get install ntfs-3g
```

---

### Post by rowbird on 2009-11-18
ntfs-3g is listed as installed in synaptic, but maybe it needs to be configured?

---

### Post by rowbird on 2009-11-18
It still does not recognize it after enabling write support.

---

### Post by JBAlaska on 2009-11-18
Was the drive disconnected from windoze without using the "safe to remove" thingy? My point is if NTFS is in a unclean condition it may not be mountable.

if you can, connect it to windoze, and do a chkdsk /f on it. You'll need to have chkdsk do it on restart If I remember right.

---

### Post by rowbird on 2009-11-18
Well, I have discovered that the drive is a fat32, and I ran the file check on it, and it found no errors. The drive functions well, and am able to boot up into XP, yet "fdisk -l" does not recognize it.

---

### Post by rowbird on 2009-11-18
This is the closest i have got to having mount recognize something.

---

### Post by rowbird on 2009-11-18
Workaround found! I installed the drive internally as a secondary IDE drive, and booted from Xubuntu. I then created a mount point in /mnt called windows, then used ths command, and voila! "sudo mount -t vfat /dev/sdb1/ /mnt/windows" The drive showed up in "fdisk -l" so the issue was with my usb adapter i presume. Thanks for the help.

---

### Post by pguedes on 2009-11-18
I've been a Ubuntu FAN since 6.10, but since I've installed 9.10, I've been having to many problems.......

Its problems with ATI Drivers.....

With Googleearth....

Disk Corruption....

System total Freezing....

Now it doesn't mount external USB drives....(it worked in the beginning but not anymore)......
I already tried to Safely remove from a Windows PC. (But this is ridiculous!!! Ubuntu should automatically solve this!)

You Name it.....I'm getting very very disappointed with UBUNTU.
It should get user friendlier from version to version....and what I get is the complete oposite........
Definitely 9.10 looks like the Vista Version of Ubuntu. (Lots of bugs and stepbacks from earlier versions)

---

### Post by rowbird on 2009-11-21
Sorry to hear you are having so many problems. I read that 9.01 has done away with hal [hardware abstract layer], so i am not surprised that there are hardware related issues. I believe they got rid of it to increase boot times. In the meantime, there are some great distros built on 9.04 that i am currently using, which are SuperOS [http://hacktolive.org/wiki/Super_OS#DVD-ISO_download]("http://hacktolive.org/wiki/Super_OS#DVD-ISO_download") and Linux Mint 7 [http://www.linuxmint.com/edition.php?id=41]("http://www.linuxmint.com/edition.php?id=41") XFCE4 community edition. I would just stick to those until the next version comes out, and hopefully by then the bugs will have been worked out. If possible maybe you could file a bug report to help out in the process ;)

---

