---
title: "Deleting a Windows partition"
date: 2011-11-08
forum: General Help
---

### Post by mudguts on 2011-11-08
So here is my problem...
I have ubuntu 11.10 installed along with Windows 7 Premium
I got a NASTY virus on my Win7 partition the other day and I plugged away for 3 days trying to fix it but am just going to scrap it and run Ubuntu full-time ... or MAYBE re-install Win7.

Here are the questions:

1.  a) If I leave the partition there, can I reinstall Windows 7 over top of them?  b) and should I format the partitions before the install?

2.  Should I / Could I just delete the partitions and make them storage?

3.  Isn't Windows 7 something that has to be installed FIRST prior to Ubuntu for the GRUB loader?

Here are my partitions.

dev/sda1 NTFS 100MB Boot
dev/sda2 NTFS 100GB Storage - (this is my storage space)
dev/sda3 NTFS 250GB - ( I think this is my Win7 partition)
dev/sda4 extended 100GB - ( I think this is my Ubuntu partition)
dev/sda5 EXT4 98GB ( no idea what this is)
dev/sda6 unknown

So... which ones can I delete?  

thanks

---

### Post by audiomick on 2011-11-08
If you re-install windows, it is likely to delete everything else on the computer, so be careful with that.

To find out which you can delete to get rid of windows, boot into a live CD and start gparted. It will give you a bit more info about what is on your partitons, and is also the tool for changing partitions. You can see mine in the screen shot, and you can see how it tells you what is what.

---

### Post by mudguts on 2011-11-08
Thanks.
I was using gparted to get an idea of the partitions.

see attached.

---

### Post by audiomick on 2011-11-09
I think that sda1 would likely be a recovery partition, and sda3 is where your Win7 is. I'm not exactly sure, however, how Win7 uses partitions. Any rate, if Win7 is to go forever, I  believe you can delete those two.

The last one, sda6, looks like it shouecogld have been your swap partition. The fact that gparted isn't recognising it indicates that something is wrong there. You should, all things being equal, be able to fix that with gparted. I am not sure, however, what has to be done to have it properly recognised by your Ubuntu install.

---

### Post by elliotn on 2011-11-09
by the look of your attachement  Windows is either in sda2 or sda3, u need to find out which one is your storage and which one have Win in it

---

### Post by Mark Phelps on 2011-11-09
The sda1 partition is the new Win7 boot partition.  That is where it stores the boot loader and associated files.  If you're going to reinstall, you can delete that.

The sda3 partition is most likely Win7 -- but to confirm, look for a file there names winload.exe.  You can also look there to see if there is a Program Files directory.  Both are indicative of a Windows OS partition.

If you're going to reinstall Win7, you should remove sda3.

Contrary to what you've been told, Windows does NOT automatically erase the contents of your hard drive when installed or reinstalled; instead, it gives you the option of choosing an existing partition or formatting free space to make a partition.

---

### Post by mudguts on 2011-11-09
Thanks.  Now if I delete it, will that effect the bootloader?  Or will it go straight into Ubuntu?

---

### Post by Matti L on 2011-11-09
Windows boot option will stay in GRUB, but you'll get an error if you select it. Run 'sudo update-grub' in terminal and that Windows line should disappear.

---

### Post by mudguts on 2011-11-09
Thanks guys.  I'll get on that deletion of the partition and just leave it ready for an install at another time for now.
I don't use Windows as much as I thought at work, so I can live without it for awhile..

---

### Post by mudguts on 2011-11-09
I deleted the partition... well, first I formatted it but it looked like the data was still there, so then I deleted it.   I'm a pretty frequent 'back-upper' so I wasn't too worried about the data.  I have a copy.

I'll let you know how the GRUB update goes.   Thanks for all your input.

---

### Post by audiomick on 2011-11-10
> **mudguts said:**
> 
I'll let you know how the GRUB update goes.   Thanks for all your input.
Your welcome. Do let us know. ;)

---

