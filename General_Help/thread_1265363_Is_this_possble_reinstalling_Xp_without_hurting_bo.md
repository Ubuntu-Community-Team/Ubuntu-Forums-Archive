---
title: "Is this possble? reinstalling Xp without hurting bootloader"
date: 2009-09-13
forum: General Help
---

### Post by T_1000 on 2009-09-13
I have 2 windows XP and one great,perfect & smoothly working Linux Ubuntu . 
Now the problem is, one of the XP has got some dll files corrupted and of week of hard attempt i couldn't get it properly working. I want to reinstall this. and other xp is full of programming softwares like vb.net,oracle, sql, php, mysql etc.

i want to keep my other Xp and linux intact and want to install new XP in-place of corrupted one. but if i install new xp, it will erase my bootloader. i don't want happen this. 

how can i proceed? is this possible?
If yes, please provide proper guidance.
help would be greatly appreciated.

---

### Post by NoaHall on 2009-09-13
Run in the corrupt one - 

Type ```
 cmd 
```
in "Run"
then write - 
```

sfc /SCANNOW

```
And insert the disk when needed. If it asks for 2003 disk or whatever, tell it to skip those files and when it's the XP version you have, insert the disk.
This will repair your core files.

---

### Post by T_1000 on 2009-09-14
@noahall, i did that already several times. what about my question. isnt this possible?

---

### Post by hetx on 2009-09-14
I don't know how you would go about doing that, but restoring the boot loader to its original pristine shape shouldn't be impossible. After the XP install (assuming you don't touch the Ubuntu partition) just pop in a Live CD, open a terminal and run

```
grub
root (hdx,y)
setup (hdz)
quit
```

Where x and y is the hard disk + partition that has the grub files (find this out by running sudo fdisk -l, boot is marked by an asterisk iirc). This would be your Ubuntu partition. Remember that sda1 = hd0,0 in grub! Grub starts counting from 0

setup (hdz) where z is the hard disk you boot from. (again, grub counts from 0 so make sure you get it right)

This will restore the boot record to original. If you get an error, you chose incorrect hd#, just check again.

I've learned this mostly by trial and error and using this thread
[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")
as a cheatsheet, so major disclaimer here. I am not an expert! Grub will throw errors at you if you try to setup boot incorrectly, but unless you fix boot record you will be unable to boot into Ubuntu without a LiveCD. Make sure you've read all you need to do it right! Good luck

---

### Post by ankspo71 on 2009-09-14
Hi,
have a look at this website. This will allow you to repair the grub if it gets deleted/overwritten. If you are reinstalling windows on the first hard drive, where the grub is located in the MBR, then this tutorial should be able to work. This worked for me when I had 2 linuxes installed, and decided to delete one of them.

Repair grub using a live cd.
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)

James.

---

### Post by T_1000 on 2009-09-14
thanks but here, y is my linux partition number.. right?

---

### Post by ankspo71 on 2009-09-14
Hi,

I think the y was just meant to be used as an example. Are all your operating systems on one hard drive? Then the answer would be maybe. If I understand correctly, you have 2 windows partitions, and a linux partition for root, possibly a separate partition for home, and then the swap file.

If Linux was installed last, (hd0,2)? is probably your root partition of Linux and you would want to install it to (hd0), at the beginning of the hard drive. If your version of windows has recovery partitions then it might throw you off a bit.

Windows is supposed to install to the first available partition, without harming the others. It might let you even select a partition to install it to too. No guarantees though, because my wife's PC has a OEM windows disk (eMachines) and doesn't have a partition manager. But, I think it is best to always make sure there is a partition there for it to be installed on.

PS. I'm not really an expert on this subject. But I have been able to restore my grub by using the above link.

James.

---

### Post by Claritux on 2009-09-14
Have a look here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

