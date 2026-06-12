---
title: "GRUB install location"
date: 2010-04-13
forum: General Help
---

### Post by jerry950 on 2010-04-13
I have been told that you can specify where to install GRUB when installing on
external hard drive. My first install of Ubuntu installed GRUB on my Windows internal
drive which prevented Windows from booting after disconnecting the Passport dirve.
I was able to fix the problem, with the help of those in the forum, but I want to
make sure that when I install on another external drive that GRUB gets installed on
that external drive. I have been told that if you use Advanced mode that that choice
is there. I will see. I have made a backup of the external drive just in case.
 
Does anyone know if Ubuntu does ask where to install GRUB during install of Ubuntu
to external drive when using Advaced mode.

---

### Post by shashanksingh on 2010-04-13
There is an advanced button in the last step of the installation that allows you to select the partition in which you want to setup GRUB.

---

### Post by jerry950 on 2010-04-14
I followed the directions but cannot boot the external iomega hard drive.
 
When booting the pc and selecting F12 like I do with the Passport bootup.
I do not get the same bootup menu with the iomega drive like I do with the
passport.
 
The passport was the first USB drive I installed Ubuntu on but had GRUB installed
on PC internal drive. Other forums users helped me fix that problem by installing
lilo which fixed the boot problem on the pc. Then installing GRUB to sdb5 on the
passport to make it bootable. This time with the iomega USB drive. I installed
Ubuntu and GRUB(I think) on the sdb5 partition of the iomega. But I do not get the
boot choice menu with F12 like I do with passport USB attached. 
I am going to attach the passport back up and test it to make sure it is okay.
 
Anyone have any ideas?

---

### Post by jerry950 on 2010-04-14
It is confirmed. Now my Passport is not a choice for booting and I do not get the
boot menu as before when using F12 at bootup.  I tried installing lilo as someone
told me to do to fix the GRUB bootup error on the pc when the passport is not
not installed through the USB. The only thing I have not do yet is to manually
run the GRUB install command he gave me.

---

### Post by oldfred on 2010-04-14
Computers boot from the MBR - sdb not the PBR or sdb5. To boot from a partition another boot loader has to be used and you chainboot into it.
Try installing grub to the MBR of sdb.

Now with some versions of Ubuntu using grub 9.04 & before or upgrades to 9.10 or grub2 with new installs of 9.10 and 10.04, you need to be sure what version of grub you are using and install the correct version. The directions are different:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by jerry950 on 2010-04-19
Hello again Fred. Let me read through some of the info you sent and see what I can 
do. I do not understand why my passport will not boot now when selecting F12 during
PC reboot. I took it home and tried it on my Dell Xp laptop and it worked okay like
it did here. The Dell is clean and has not been exposed to Ubuntu installers or other. 
 
Something must have happend to the Windows laptop here at work that I use to be 
able to boot from as it does from home. I suspect that something happen on the PC 
when I installed Ubuntu on the external Iomega drive. Even though I installed GRUB 
on the Iomega as prescribed by others instead of on the PC.

---

### Post by oldfred on 2010-04-19
Generally everything is based on UUIDs so drive number does not matter. But grub may need to know that the drive is sda or sdb. If you plug the external into another system with a different number of drives or the BIOS makes it something other than sdb then you may have problems. I have some users with an external inserted as sda and one fellow had it has sdf with no other drives.

---

### Post by jerry950 on 2010-04-20
Fred, I read through the link you posted. At the end for 9.10 he states:
 
---
Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.
---
 
Replace what?  I think he is referring to installing on local PC disk sda and not external
sdb in my case. 
 
I'll post some info when I can. I'm still trying to understand what is what here.

---

### Post by jerry950 on 2010-04-20
buntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa786d6ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710        7751    38117520    f  W95 Ext'd (LBA)
/dev/sda5            2710        7751    38117488+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      118202   949457533+   7  HPFS/NTFS
/dev/sdb2          118203      121601    27302467+   5  Extended
/dev/sdb5   *      118203      121455    26129691   83  Linux
/dev/sdb6          121456      121601     1172713+  82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo mkdir /media/sdb5
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /media/sdb5

ubuntu@ubuntu:~$ ls /media/sdb5
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdb5 /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /media/sdb5/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb

---

### Post by jerry950 on 2010-04-20
The last post was for the iomega external disk. The re-install of GRUB fixed the
booting problems with it.

The Passport however. Boots from my Dell laptop at home but not on the IBM Thinkpad
here that I just booted the Iomega drive from. I installed Ubuntu from the Thinkpad and
everything seemed to be working okay. Now when doing fdisk -l is does not show a
linux partition. ??  I do not know what to do expect maybe re-install Ubuntu. How do
I get rid of partition /dev/sdb1 or re-use it?  Why does it boot from home if not here
on this PC?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa786d6ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710        7751    38117520    f  W95 Ext'd (LBA)
/dev/sda5            2710        7751    38117488+   7  HPFS/NTFS

Disk /dev/sdb: 749.5 GB, 749452918784 bytes
255 heads, 63 sectors/track, 91115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000791e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91116   731886592    7  HPFS/NTFS

---

### Post by oldfred on 2010-04-20
Your second entry does not even display the extended partition?? It looks like your hard drive is smaller because it is missing the extended partition.

I do not think the issue is sdb1 but perhaps the extended is not set up totally correctly.

Some BIOS do not let you boot unless the boot flag is on a primary partition. Windows requires a boot flag (active partition), linux/grub does not use it, but some BIOS seem to think only windows so they want it.

I would try moving boot flag from sdb5 to sdb1. (But I am not sure if that is the total problem).

set boot flag on for sdb1 (off for others)
sudo sfdisk -A2 /dev/sdb1

You can also use gparted or disk utility. Make sure you only have one boot flag per drive.

---

### Post by jerry950 on 2010-04-20
Ignore my last post. It was the wrong Passport. But. the Passport that does have the
linux installed on it, I re-installed GRUB but USB is not an option to select as bootup
when selecting F12 on the PC.  Here is the fdisk -l on the Passport that boots okay
from home pc.  And further down is the menu I get when selecting F12 for booting.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa786d6ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710        7751    38117520    f  W95 Ext'd (LBA)
/dev/sda5            2710        7751    38117488+   7  HPFS/NTFS

Disk /dev/sdb: 319.4 GB, 319370035200 bytes
255 heads, 63 sectors/track, 38827 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00035f28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19447   156207003+   7  HPFS/NTFS
/dev/sdb2           19448       38827   155669850    5  Extended
/dev/sdb5           19448       38456   152689761   83  Linux
/dev/sdb6           38457       38827     2980026   82  Linux swap / Solaris
---------------------

And this is all I get when selecting F12. Where is -USB?

2. ATAPI  CD0: DVD/CDRW
4. ATA HDD0: HTS541060G9SA00
5. PCI LAN: IBA GE Slot 0200

---

### Post by oldfred on 2010-04-20
On my desktop the choices were hard drive, cd, floppy and a long list of USB devices USB floppy, USB CD etc. None of the USB devices worked but on one day I had the USB key in and selected boot from hard drive and among my hard drive choices was the USB key. It was not a USB device but a hard drive in the BIOS menu.

---

### Post by jerry950 on 2010-04-22
I do not know why USB is not being listed as a choice for booting. When I select F1 to
go into BIOS. I see 7 orders of booting and two that are excluded. But with F12 only
the ones I listed above. I do not know how to make it list USB as it did before for
booting from. Is there something wrong with BIOS?
 
Boot order
 
1. USB FDD
2. ATAPI
3. USB CD
4. ATA HDD0
5. PCI LAN
6. -USB HDD
7 ATA HDD1
 
Excluded:
ATA HDD2
ATAPI CD1

---

### Post by oldfred on 2010-04-22
What does USB HDD get you? That sounds like an external drive.

---

### Post by jerry950 on 2010-04-23
I think I found the problem. A USB port is not a USB port.
This laptop is connected to a docking station that has two USB ports on the left side
and two in the back. My laptop has one on the left side and two on the right.
I moved the USB cable to the one on the left of the laptop and when I boot with F12 
then it shows up as a bootable selection. Another Passport that developer gave me 
that has Ubuntu installed also boots okay from this laptop USB port.
 
I guess a USB port is not a USB port for anything you want to plug into it.

---

