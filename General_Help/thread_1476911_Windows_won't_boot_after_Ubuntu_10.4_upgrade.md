---
title: "Windows won't boot after Ubuntu 10.4 upgrade"
date: 2010-05-08
forum: General Help
---

### Post by techbyter on 2010-05-08
I have a 64-bit dual-boot system. During the Ubuntu upgrade to 10.4, the  installer crashed. GRUB shows the new Ubuntu installation and the  default boot item is Windows 7, but Windows won't start.

I have a  Windows backup (Acronis) but afer I select any option from the Acronis  CD options menu, the keyboard and mouse are no longer recognized. The  keyboard and mouse are fine and work as expected when attached to a  notebook computer.

The computer has 4 internal hard drives and  one external USB drive. I have tried changing the boot order with the  hope that Windows would start, but have had no luck.

sda1 =  1.00TB = "System Reserved" - Ubuntu (105GB), Windows (316GB), Data3 (579GB),  Ext4 (46), Swap (8GB), Ext4 (52GB)
sdb1 = 1.50TB = Data2 (734GB), Media  (766GB)
sdc1 = 0.25TB = Internal Backup (250GB)
sdd1 = 0.50TB = Data1  (392GB), Ext3 (103GB), Swap (4GB)
sde1 = 0.50TB = USB external backup (500GB)

I  can get to the Ubuntu login screen, but Windows will not boot. I can  log on to Ubuntu.

Possible problem: I may have overwritten the  Windows boot loader with another copy of GRUB, but that doesn't really  explain the problem with the mouse and keyboard. Legacy USB support is  enabled in CMOS and the keyboard does work at boot time (F2 works for  CMOS access).

I have tried booting to the Windows 7 DVD, but  choosing the repair option results in a message that the installed  version of Windows (Win7/64-bit) doesn't match the DVD version  (Win7/64-bit).

I could really use some help with this one!

---

### Post by booshire on 2010-05-08
Hello -

What is the error grub gives you when it will not boot to Windows? Or is there an error? If you did write over the windows boot, you can go into the recovery console and type in "fixmbr" to re-write the MBR. Then you will have to re-install or fix grub. Usually when this happens to me I have to hunt around using grub to find the correct Windows partition and then update the grub conf file.

---

### Post by FahadMKS on 2010-05-08
There are many of the issues with the Windows 64 bit OS  It is always recommended to use the single OS boot so that there will be no issues.

---

### Post by techbyter on 2010-05-08
No error message. Just a blank screen. 
I have run the following:
bootsect /nt60 ALL 
bootsect /nt60 ALL /mbr
bootsect /nt60 ALL /force /mbr

(bootsect is the replacement for "fdisk /mbr")

Now GRUB is gone, but Windows still won't start.

8 May 10 at 16:50:20: Resolution

Reinstall Windows.
Remove Ubuntu (probably permanently) from the production system. I will continue to work with Ubuntu on the notebook, which is not a mission-critical machine.

---

