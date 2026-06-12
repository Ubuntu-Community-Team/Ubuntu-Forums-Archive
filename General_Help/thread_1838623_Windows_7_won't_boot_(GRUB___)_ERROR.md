---
title: "Windows 7 won't boot (GRUB _ ) ERROR"
date: 2011-09-04
forum: General Help
---

### Post by hufnagel on 2011-09-04
I had a Compaq Presario V2000 series with Ubuntu 9.10 and Windows 7 installed.
I decided to delete Ubuntu and accidentally deleted both the Ubuntu and GRUB partitions.
I managed to get some kind of OS running on my laptop by installing the latest Ubuntu 11.04 with a CD. GRUB came back again, but when I try to boot into Windows 7 , it just comes up with "GRUB _" with the "_" blinking.

How can I get Windows 7 to boot again? I could see all the files from Windows 7 by using Ubuntu so it should still be alive...

---

### Post by YesWeCan on 2011-09-04
Boot live Ubuntu CD
sudo fdisk -l
check you drive name, I'll assume it is sda
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

This restores the normal MBR boot code and should enable Win to boot unless there is any damage to the other boot files.

---

### Post by decrepit on 2011-09-04
try
sudo update-grub

---

### Post by gandaran on 2011-09-04
> How can I get Windows 7 to boot again?
did you install grub to any other partition than the default install to disk MBR?

---

### Post by hufnagel on 2011-09-04
I only installed Grub through the Linux Ubuntu CD and I'm not really sure where it was installed.

---

### Post by hufnagel on 2011-09-04
> **YesWeCan said:**
> Boot live Ubuntu CD
sudo fdisk -l
check you drive name, I'll assume it is sda
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

This restores the normal MBR boot code and should enable Win to boot unless there is any damage to the other boot files.I tried this, but I couldn't set the MBR to the Windows partition.

---

### Post by gandaran on 2011-09-04
> **hufnagel said:**
> I only installed Grub through the Linux Ubuntu CD and I'm not really sure where it was installed.
well, if you didn't specify a location then it's correctly installed in the disk MBR section and windows should be booting, do you still have the windows 7 boot loader (100MG) partition on disk or did you erase it by mistake?

---

### Post by YesWeCan on 2011-09-04
> **hufnagel said:**
> I tried this, but I couldn't set the MBR to the Windows partition.
I don't understand what you mean.
There is only one place for the MBR and it is not in any partitions. So if your disk name is sda the location of the MBR is denoted as sda, not sda1 or sda2.

Better download and run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post RESULTS.txt in code tags (highlight then click #).

---

