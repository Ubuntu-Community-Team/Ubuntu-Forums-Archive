---
title: "Run Ubuntu without USB Drive &amp; Where to Put Partition"
date: 2010-01-07
forum: General Help
---

### Post by babitweety06 on 2010-01-07
When starting up my dell mini 9 it will freeze at the loading screen and about 2 min later it will say that the there is basically no operating system. Someone on here told me to reinstall Ubuntu so installed it to a USB and while trying to install I would get stuck on the partition page. There would be no option to select a partition or even to create one. So i quit the installation and manually created a partition through gparted. Im not sure if I am mounting the partitions in the right place but I need help and can someone let me know what type of partitions do i need, where to mount them. I dont know exactly what i did but i would run 2 USB's with Ubuntu on them at one time. One will run the Ubuntu and one I was trying to create a partition with but I just need serious help and can someone help me. I think I would be doing the right thing at the partition page it will let me install ubuntu but its not saving to the computer because when i take the USB out UBUNTU will not work. So please can someone let me know who to install ubuntu so that i dont have to use the USB.

---

### Post by C.S.Cameron on 2010-01-07
What version are you trying to install?
I recall at one time that when installing from flash drive to flash drive or SSD the installer would get confused and grub would get installed in the wrong place so the flash drive would need to be plugged in to boot.
This was easy to fix by reinstalling grub.
Check this page:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by babitweety06 on 2010-01-07
*find /boot/grub/stage1*
 
when i typed this in, it says error 15: file not found. im stuck

---

### Post by C.S.Cameron on 2010-01-07
That means you don't have an Ubuntu O/S on the computer.
What happens when you get to Step 4 of 6, Prepare disk space?
There should be two options:
Erase and use the entire disk.
Specify partitions manually.
if you chouse the first option the program should partition and format your SSD automatically.
if you wish to format your SSD prior to install I would format the whole drive ext3.

---

### Post by babitweety06 on 2010-01-07
i dont know if i am doing something wrong.  But i have reinstalled it using the entire disk and i am still getting the error message

---

