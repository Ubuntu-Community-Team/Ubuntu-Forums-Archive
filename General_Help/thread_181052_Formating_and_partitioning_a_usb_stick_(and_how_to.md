---
title: "Formating and partitioning a usb stick (and how to get root priv.)"
date: 2006-05-23
forum: General Help
---

### Post by zainka on 2006-05-23
Hi

I have a router from Asus (wl500g) which runs linux kernal (much like linksys does) and from Putty I can access the samba rythms of my router and perfome quite a lot of things and thangs to make it perfect for my needs if I ahd the skills. However, at a point I needed to install the ipkg package which required me to unmount the device  prior to have this update working because I needed to make an ext2 or 3 partition on the USB stick connected to the router. I never managed to do this  since this again required me to unmount the device which I yet again was denied since the device seems to always be bussy  and killing the service which I knew was using the usb stick never seemed to work either ("killall stupid-ftp" for those who are familiar with asus routers). So much for this.. Then you may ask why I put this cinda question in Ubuntu forum??

Thing is that I have got this brilliant idea where I moved the USB sticker to my computer running Ubuntu 5.10 (Gnome i belive) and where I intended to use Ubuntu to format the stick or atleast make a new partition with ext2 or 3 file system format. The stick is by a windows xp thingy earlier been formated as fat32 (its a corsair 512MB stick anyway). But do you think this would work??? Aaa, naah! Id didnt' ](*,) . First of all, when using 'Disk manager' I cant access the format button (greyed out) and it says that the format is vfat (fair enough). Second is that disk manager says that the device name is /dev/sdb (also fair enough). BUT, when switching to 'terminal' and running command 'df' the device name is /dev/sdb1 and where did the number 1 come from, (which one is right? sdb or sdb1), Also, when I tries to umount the device the system says I am not root, cracy.  Even the command "I want to be root" wont work (not recognized) :-D 

Thing is, can someone help me to understand how to gain controll over my USB stick and how to format it? And offcource, how to be root. I mean, I installed the Linux thing and now it wont give me root status,.?

As you might understand, I am not a wery skilled linux user but I realy want this thing up and working so please help me if you can

Thanks a lot in advance

Best regards
Z

---

### Post by aysiu on 2006-05-23
You don't need to convert a USB stick to Ext3 in order to use it. FAT16 or FAT32 should work just fine.

You cannot format partitions or drives that are mounted.

To unmount as root, paste this command into the terminal: ```
sudo umount /dev/sdb1
```

/dev/sdb refers to the whole drive. /dev/sdb1 refers to the first partition on the /dev/sdb drive. If there's only one partition, it's /dev/sdb1.

---

### Post by nanotube on 2006-05-23
if you want to learn more about "root" and permissions, read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by zainka on 2006-05-23
wooha! Thats fast responce indeed! In wl500g forum you can wait for ages to get a responce. Il dig into the wiki and thank you both for responce.

However, according to wl500g ipkg tutorial I **need** to have an ext 2 or 3 partition to make the hingy work properly, Or actualy, when reading "known" partition types it is an linux swap thing). I know that fat32/16 is suficient everywhere else but not for that ipkg package, silly? Yes. Can I do something with it?... N.. Yes, but then I need to recompile the whole linux /ipkg thing my self to be used with other file systems, so No..

Thanks again
Z

---

### Post by halfvolle melk on 2006-05-23
Maybe something along the line of this will work
```
mke2fs /dev/sdb1
```
You may want to read the man page for details on mke2fs.

---

