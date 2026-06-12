---
title: "expand filesystem"
date: 2010-05-03
forum: General Help
---

### Post by SoulSurvivor on 2010-05-03
Hi,
I've expanded my partition /dev/sda3 which hold ubuntu.  Now I believe i need to somehow expand the amount of space Ubuntu sees (I guess the filesystem?)  How would I do that?

Some details:
3 partitions
sda1 : fat32; small partition with some utility stuff that was already on my laptop when I bought it
sda2 : NTFS; boot partition, holds windows XP Professional as well
sda3 : NTFS; holds Ubuntu

my drive is 120 GB SATA.

I used Gparted to expand sda3 and possibly sda2 (don't remember) but Ubuntu doesn't seem to be detecting the extra free space.  I need it to do that.

Thanks

---

### Post by SoulSurvivor on 2010-05-03
update:
I reinstalled windows and got it working.  It says that the 3rd partition (the one with Ubuntu) only has about 10 gb meaning it has something like 20 or 30 GB free.  But Ubuntu only reads 2 GB free and thinks there is a lot more space taken up on the partition.  How do I fix this??

Help would be much appreciated

---

### Post by coffeecat on 2010-05-03
> **SoulSurvivor said:**
> sda3 : NTFS; holds Ubuntu

Are you using Wubi?

---

### Post by SoulSurvivor on 2010-05-03
EDIT: Yes, I believe so.  I used a CD to install I think...but I did it inside of windows so ultimately I guess that would have to have been Wubi or something.

BEFORE EDIT: Not sure.  I'll read up on wubi.  I've seen it mentioned before but don't know what it is.  I installed Ubuntu in Win XP though... not sure if that helps.  There were some file on that partition with names similar to wubi.  Is that something used to install or boot Ubuntu..?  I'll see what I can find to answer that

---

### Post by coffeecat on 2010-05-03
The reason I asked is that Ubuntu can't run in a NTFS filesystem, so it looks as though you might be using Wubi. Wubi works by making a virtual hard drive as a single file in the Windows NTFS filesystem, but within that single file is an emulated Linux filesystem for Ubuntu to work in. The easy way to tell if you're running under Wubi is to look in your Windows filesystem. Do you have a C:\ubuntu folder? Or D:\ubuntu (or E:\ or F:\...) if in another partitition? If yes, you have Wubi. 

The problem with Wubi is the virtual-drive/single-file. Once its size has been determined, it can't be changed - or so I believe. I've little experience of Wubi. It's a good way of trying out Ubuntu in the short term, but you get inferior peformance, so most people prefer to install Ubuntu on its own dedicated partition.

---

### Post by jerome1232 on 2010-05-03
Well there are ways to expand a wubi filesystem, you basically create a dummy file on the windows drive of the correct size (fill it with zero's) you can use dd to create a big file filled with zeros,then mount it as another drive under ubuntu. There are other methods too, I think you can even resize the filesystems.

There's a how-to of sorts in the wubi wiki. Have a look there to get some ideas.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by SoulSurvivor on 2010-05-03
ok awesome! Thanks for the info.
could you point me to a good tut on how to install it on it's own partition?

the way I understand it, I should
uninstall from Windows
install from CD (and format partition in the process)

Anything special I need to do or have a heads up about?  Do I need to do anything special for GRUB?

Thanks for the help coffeecat

---

### Post by coffeecat on 2010-05-03
> **SoulSurvivor said:**
> could you point me to a good tut on how to install it on it's own partition?

Here's a good start:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Be aware that that shows the Karmic (9.10) installer. The Lucid one is almost the same except for when you first start the CD. You get only a couple of little icons at the bottom of the screen for a few seconds. If you do nothing you are taken straight to the installer. If you want the live desktop session, tap the space or enter key when the icons appear and the language screen appears as in that link.

> **SoulSurvivor said:**
> Anything special I need to do or have a heads up about?  Do I need to do anything special for GRUB?

The installer will take care of grub. You need to know that grub stage 1 overwrites the mbr, so if you ever decide to get rid of Ubuntu and return to Windows (you won't :wink:) you'll need a way or repairing the Windows mbr. There are several methods, repeatedly posted on these forums.

What I would advise is to boot up with the live CD, go to Applications > Accessories > Terminal and do:

```
sudo fdisk -l
```Post the output of this in another support thread to get advice on partitioning. If 6 people answer you'll get 12 different pieces of advice (:wink:), but it will be useful to clarify your own mind as to what you want.

Good luck!

---

