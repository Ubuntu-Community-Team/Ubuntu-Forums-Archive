---
title: "Windows 7 installed cannot access linux"
date: 2009-12-01
forum: General Help
---

### Post by Wish4Me on 2009-12-01
I had my Kubuntu setup with all my files, but I installed Windows 7 and now I cannot access Kubuntu. I have the Kubuntu Distro Disc but I don't know how to fix it.

---

### Post by MelDJ on 2009-12-01
is grub still there? 
if you select kubuntu, are there any errors?

---

### Post by Ahadiel on 2009-12-01
See if this helps: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Wish4Me on 2009-12-01
> **Ahadiel said:**
> See if this helps: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Grub seems to be gone. Changed or overwritten by Windows 7. The system boots straight to Windows 7.

EDIT: I wasn't mounting the partions but I am not sure how to mount the partions.

---

### Post by MelDJ on 2009-12-01
is the kubuntu partition still there?
looking at it, i think you have accidently deleted it

---

### Post by Wish4Me on 2009-12-01
I'm on the Kubuntu live cd now.

I put in sudo fdisk -l and got:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078458                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10942    87891583+  83  Linux 
/dev/sda2           10943       12158     9767520    5  Extended
/dev/sda3   *       12159       12171      102400    7  HPFS/NTFS
/dev/sda4           12171       24907   102297600    7  HPFS/NTFS
/dev/sda5           10943       12158     9767488+  82  Linux swap / Solaris

```

The Kubuntu Partion is still there.
After I typed the fdisk I typed:
```
sudo mkdir /media/root

```
and the terminal went to the next line.

Then I typed out sudo mount /dev/sda2 /media/root but got:
```
mount: you must specify the filesystem type
```

I'm trying to follow that guide but I am having trouble mounting it.

I don't know which is which out of sda1 and sda2.

---

### Post by Leppie on 2009-12-02
try mounting like this:
```
$sudo mount /dev/sda1 /media/root
```

sda1 is your linux partition.

---

### Post by Wish4Me on 2009-12-02
Should I change the ntfs to ext4? I installed Kubuntu under ext4.

I did both. It said it wasn't ntfs which I knew. But it also gave me this for ext4:

wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

EDIT:
sudo mount -t ext4 /dev/sda1 /media/root seemed to work.
It just went to the next line when i typed it.

---

### Post by MelDJ on 2009-12-02
use gparted, right click the kubuntu partition and press manage flags. then check boot. reboot and see if it boots into kubuntu

---

### Post by Nburnes on 2009-12-02
If you don't want to install GRUB over again, you can just use one of the EasyBCD betas to keep Windows bootloader and then just add an entry for Kubuntu.

---

### Post by switch10 on 2009-12-02
when dual booting always install windows first.  I learned that the hard way too.  It just overwrites your boot manager.  all your files should still be there when you put in a live CD.  get all your files and settings off and reinstall kubuntu.

EDIT  all your files should be there unless you wrote over your kubuntu partition

---

### Post by Wish4Me on 2009-12-02
Ok. Used the guide and Leppie's help to mount. I reinstalled Grub and was able to get into Kubuntu. Thank you guys. Now I just need to readd windows.

EDIT:

Okay help. That guide says to use:
kdesu kate /boot/grub/menu.lst
to add windows to grub but my terminal says:
kdesu: command not found

EDIT2: Basically since I am using Grub 2 that guide is old. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Trying to figure out how to add windows to the list. Please help if you know how.

---

### Post by wilee-nilee on 2009-12-02
sudo update-grub

---

### Post by Wish4Me on 2009-12-02
Wow. That easy? Thanks.

---

### Post by wilee-nilee on 2009-12-02
> **Wish4Me said:**
> Wow. That easy? Thanks.

Hopefully, did that fix it? The others provided the dirty hard work.

---

### Post by Leppie on 2009-12-02
> **Wish4Me said:**
> wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


reading your fdisk -l output, sda2 is the extended partition. it only hosts sda5, so cannot be mounted as a partition in itself.

---

