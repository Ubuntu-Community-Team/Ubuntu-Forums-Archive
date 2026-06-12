---
title: "USB Flah Drive problem!  help!"
date: 2009-08-22
forum: General Help
---

### Post by kofte on 2009-08-22
Hello.

I'm having a problem. Recently, I had to format my hard drive and re-install Windows. What I ended up doing by mistake was, after I had popped in the XP Pro CD and got to the part where you have to delete and create a new partition, I had accidentally formatted my 8GB OCZ  USB flashdrive that was inserted into my computer at the time. I had quickly realized what I had done and so I tried to plug it into a Windows PC.

After doing so, I tried to open it, but it won't work. It says "You must format this device before you can use it" or something of like that. So, I try formatting however it gives me  the error message; "Windows cannot format this device". 

I was told I must format it as a FAT16  or FAT 32 drive under Linux? 

I'm at a loss and I would appreciate any help!

Thank you.


EDIT: If it helps. I had used the same USB flash drive with Ubuntu before. I had plugged it in and it recognized it without a problem before I had accidentaly formatted it. Now it recognizes it when I plug it in, but once I double click on it, it says "Unable to mount location: Can't mount".

Note: I'm using Ubuntu right now so I would be able to follow any instructions requiring Linux.

---

### Post by hyperdude111 on 2009-08-22
Don't worry the solution is quite simple. 

Go Applications-accessories-terminal

Type 
```
sudo apt-get install gparted 
```
Then enter your password, dont worry when nothing comes up when you type your password thats supposed to happen.

Then go System-Administration-Partition Editor

Up will come an application with information about all attached volumes. On the right hand side select the drop-down menu and go to /dev/sdb (i think)

This will change the details on the main window, now make sure the partition manager has selected your USB drive and not any other device. (Check that the size is equal to your usb size)

Then select the long bar in the middle and delete it. 
Then select the empty space and chose the new option.
Create the new partition to take up all empty space then change the filesystem to FAT32

After that chose  ADD and then APPLY. Wait for it to finish (not too long) then your sub drive is ready. You can now use it again in Windows Mac and Linux.

---

### Post by JC Cheloven on 2009-08-22
- install gparted from the repository (if you already haven't)
- plug the usb stick
- run gparted (menu : system -> partition editor)
- unmount the drive (but not unplug it)
- delete whatever partition is in the drive (CAUTION: select the right one from the upper right corner; something as /dev/sdc)
- apply
- device -> create partition table
- click on the empty space of the drive (the grey area representing the drive)
- new
- choose primary, fat32, and a label (if you wish)
- apply

You're done. Unplug, plug again and use it ;-)

---

### Post by kofte on 2009-08-22
Gparted to the rescue! 

I tried using cfdisk but it wasn't showing anything about /dev/sdb (the USB flashdrive).

Thanks a lot, fellas. That was quick and easy!

Have a good night.

---

