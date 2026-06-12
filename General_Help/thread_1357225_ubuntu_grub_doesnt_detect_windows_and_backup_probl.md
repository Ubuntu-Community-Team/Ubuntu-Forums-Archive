---
title: "ubuntu grub doesnt detect windows and backup problem"
date: 2009-12-17
forum: General Help
---

### Post by evelin on 2009-12-17
1.hello, i installed windows xp (not directly from the disc, i installed it via restoring partition) , and i had ubuntu 910 already installed, so  i tried reinstalling the grub but nothing it doesnt detect windows, how do i add the windows boot to the grub

pos: i cant format neither xp or ubuntu for some personal problems

2.what is the best program for making a backup of all ubuntu partition.

pos:if you tell me clonezilla, can you give me a good tutorial, cause clonezilla always fails me when restoring an image

thanks

---

### Post by amsterdamharu on 2009-12-17
I have this in my menu.lst to boot windows:
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

To find the correct root you can go to commandline in grub (press c in the menu)
then type
find /boot.ini
you might get a response like hd(0,0)
That means windows is on hardisk 1 partition 1
In boot.ini you have to do the same:
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

The above means partiotion 1 of disk 1
If you're not sure what partition it is you can make a menu like this in the boot.ini:

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="win partition 2" 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="win partition 3" 


About your backup I am not sure, you can rar and gzip it. Works for me but I have all my ubuntu stuff on one partition. I start with a usb (TRK) mount my ubuntu and back it up:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

As for windows I use ghost, boot from the same usb using memdisk and a dos image.

You might considor backing up your mbr and partition tables using dd.
[http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/](http://embraceubuntu.com/2005/10/20/backing-up-the-mbr/)
Make sure you put that backup on a bootable usb because a broken mbr cannot boot and a broken partition table cannot show you the files on the harddisk(s)
AND BE CAREFUL WITH DD COMMAND, A MISTAKE AND YOU CAN DESTROY THE DATA ON THE HARDDISK

---

### Post by evelin on 2009-12-17
hello, i have the new grub i think is 1.94 or 97 not sure, i dont find the menu.lst, i think this new version changed to another name or else, do u know where do i find it

---

### Post by amsterdamharu on 2009-12-17
/boot/grub/grub.conf
or
/boot/grub/menu.lst

When you edit it make sure you don't mock it up becuase you won't be able to boot anymore untill you fix it.

---

