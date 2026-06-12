---
title: "Sharing windows user files with ubuntu 9.10 x64..."
date: 2010-04-28
forum: General Help
---

### Post by Hydrokys on 2010-04-28
I have a 500gb hdd and a 320gb hdd . i want to dual boot with windows 7 on the 500. I usually make 4 partitions for windows - 1. windows 2. programs 3. games 4. data- and put ubuntu on the 2nd hard drive. I am doing a clean install and was wondering how i could do this if even possible.

---

### Post by WinterRain on 2010-04-28
Very possible. Just make your partitions on the windows drive, install windows, then install ubuntu on the other drive, and choose "use whole drive" during installation. 

Or do like I do, and install your windows, then unplug the windows drive before installing ubuntu. I then hit F12 at startup to choose which drive to boot. I do it this way because I don't want GRUB to handle anything.

Just make sure to put windows on the first partition of the drive, otherwise it won't install.

---

### Post by recluce on 2010-04-29
> **WinterRain said:**
> 
Just make sure to put windows on the first partition of the drive, otherwise it won't install.

Why would that be? I have not had Windows on "Drive C" or sda1 since 2002. Currently, I have Windows XP on sda5 ("Drive D") and Windows 7 on sda7 ("Drive F"). It still helps against some really stupid malware that assumes a system path of C:\WINDOWS.

---

### Post by oldfred on 2010-04-29
Windows in general:
Windows is supposed to be on a primary partition that is active (boot flag), second installs can be in logical partitions but rely on the primary partition for booting as they have moved boot files into the active partition. I have seen only one or two cases where one of the experts here converted a logical to directly boot windows via grub.

For the OP:
Since you understand partitions, you should install Ubuntu on the second drive. Normal installs only require / (root) and swap. But many recommend /home for user data & settings to make it easy to do a clean reinstall a new version of Ubuntu and retain settings & data. Some also add data partitions, but you already have lots of data in NTFS partitions that Ubuntu will easily read & write.

---

