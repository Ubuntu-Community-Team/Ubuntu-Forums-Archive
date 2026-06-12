---
title: "Can't recover Ubuntu after installing Windows"
date: 2010-09-29
forum: General Help
---

### Post by kfriddile on 2010-09-29
I have two drives in my system with Windows7 installed on the first one (sda) and Ubuntu installed on the second one (sdb).  I had to reinstall Windows and now I of course can't access Ubuntu since the MBR was overwritten by the Windows installer.  I followed the LiveCD recovery method described at

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and it didn't work.  When I rebooted after doing a grub-install on sda, I was simply given a Grub command line with no menu or anything.  grub-install said it completed successfully and had no errors.  What exactly do I need to do to get Grub set up correctly so I can access both OSes?

---

### Post by andrewthomas on 2010-09-29
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by garvinrick4 on 2010-09-29
for sda install.
```
sudo fdisk -l
``` lower case L
find which is ubuntu install. lets say sda1 for this.
```
sudo mkdir /media/root
```
```
sudo mount /dev/sda1 /media/root
```
```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```
```
sudo umount /media/root
```
Boot into hard drive install of Ubuntu
```
sudo update-grub
```
There will be an option in BIOS to set which to boot first HDD/CD or USB
And there will be an option to boot anyone at boot time in BIOS.

---

### Post by kfriddile on 2010-09-29
> **garvinrick4 said:**
> for sda install.
```
sudo fdisk -l
``` lower case L
find which is ubuntu install. lets say sda1 for this.
```
sudo mkdir /media/root
```
```
sudo mount /dev/sda1 /media/root
```
```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```
```
sudo umount /media/root
```
Boot into hard drive install of Ubuntu
```
sudo update-grub
```
There will be an option in BIOS to set which to boot first HDD/CD or USB
And there will be an option to boot anyone at boot time in BIOS.

This BIOS actually doesn't allow me to select *which* hard drive to boot from, it just allows me to boot from "CD" or "hard drive".  Booting from "hard drive" always boots from the first one which is where Windows is installed.  It's a laptop and the BIOS options are rather limited.

---

### Post by garvinrick4 on 2010-09-29
Use install CD as Try Ubuntu and run sudo fdisk -l in a terminal will
show all drives. Post it here.

---

### Post by kfriddile on 2010-09-29
> **garvinrick4 said:**
> Use install CD as Try Ubuntu and run sudo fdisk -l in a terminal will
show all drives. Post it here.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53d9c11a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e165

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29165   234259456   83  Linux
/dev/sdb2           29165       30402     9936897    5  Extended
/dev/sdb5           29165       30402     9936896   82  Linux swap / Solaris
```

---

### Post by Mark Phelps on 2010-09-29
IF you can still boot Win7 OK, I would recommend you do the following:
1) Obtain an Ubuntu LiveCD (desktop version is OK)
2) Disconnect the Win7 drive
3) Put Ubuntu LiveCD into the CD/DVD drive
4) Follow the instructions in the link below to reinstall GRUB:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

5) Reboot using only the Ubuntu drive.  IT should boot OK now.
6) Reconnect the Win7 drive, but boot from the Ubuntu drive
7) Boot into Ubuntu.  Open a terminal and enter "sudo update-grub".  This should regenerate the GRUB menu and include an option for Win7
8) Reboot

You should now have a GRUB menu with entries for Win7 and Ubuntu.

---

### Post by kfriddile on 2010-09-29
> **Mark Phelps said:**
> IF you can still boot Win7 OK, I would recommend you do the following:
1) Obtain an Ubuntu LiveCD (desktop version is OK)
2) Disconnect the Win7 drive
3) Put Ubuntu LiveCD into the CD/DVD drive
4) Follow the instructions in the link below to reinstall GRUB:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

5) Reboot using only the Ubuntu drive.  IT should boot OK now.
6) Reconnect the Win7 drive, but boot from the Ubuntu drive
7) Boot into Ubuntu.  Open a terminal and enter "sudo update-grub".  This should regenerate the GRUB menu and include an option for Win7
8) Reboot

You should now have a GRUB menu with entries for Win7 and Ubuntu.

Ya, that would be nice, but disconnecting individual drives is a pain as this is a laptop.  Also, as I said previously, the BIOS doesn't give me to option to select which of the two hard drives to boot from.  I can only boot from sda which is where Windows is installed.

---

### Post by Quackers on 2010-09-29
I have a laptop with 2 hard drives and am also unable to select which hard drive is looked at first. I have Vista on sda and Ubuntu on sdb. My system won't show a grub menu unless grub is installed in the MBR of both drives.
Try installing Grub to sdb.

---

### Post by garvinrick4 on 2010-09-29
It is a laptop so your sdb drive the one with linux is a external USB drive correct.

---

### Post by kfriddile on 2010-09-29
> **garvinrick4 said:**
> It is a laptop so your sdb drive the one with linux is a external USB drive correct.

No, the laptop actually has two internal hard drives.

---

### Post by kfriddile on 2010-09-29
> **Quackers said:**
> I have a laptop with 2 hard drives and am also unable to select which hard drive is looked at first. I have Vista on sda and Ubuntu on sdb. My system won't show a grub menu unless grub is installed in the MBR of both drives.
Try installing Grub to sdb.

That doesn't work.  Right now, I've reinstalled the Windows MBR on sda so that Windows will boot and I can post here, but Ubuntu is inaccessible of course.

---

### Post by Quackers on 2010-09-29
To fix mine I followed drs305's guide and installed Grub2 to both sda and sdb from a Ubuntu Live CD.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by kfriddile on 2010-09-29
> **Quackers said:**
> To fix mine I followed drs305's guide and installed Grub2 to both sda and sdb from a Ubuntu Live CD.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

That's similar to what I did before that resulted in me getting the grub command line after rebooting.  Is it maybe because I hadn't yet run update-grub?  How can I run update-grub when I can't reboot into Ubuntu?

---

### Post by Quackers on 2010-09-29
You would need to boot from an Ubuntu Live CD and select "Try Ubuntu" then run the commands given in that link, after chrooting into your existing system (the instructions for which are in that link).

---

### Post by kfriddile on 2010-09-29
> **Quackers said:**
> You would need to boot from an Ubuntu Live CD and select "Try Ubuntu" then run the commands given in that link, after chrooting into your existing system (the instructions for which are in that link).

One more question.  Which disk to you boot from?  Your Windows drive (sda) or your linux drive (sdb)?

---

### Post by Quackers on 2010-09-29
My bios seems to be set to look at the first drive first. I have no options to change that (courtesy of Sony's insistence on locking the bios).

---

