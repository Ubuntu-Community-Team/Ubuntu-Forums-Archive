---
title: "Would fat32/ntfs home folder make ubuntu significantly slower?"
date: 2011-09-19
forum: General Help
---

### Post by garfieldpbj on 2011-09-19
Hi

I am running ubuntu 99.9 % of the time, but some times it is necessary to run windows (even though I now that wine, should have become a lot better since I used it years ago)...

For this reason it would be nice if my "standard data", for examples the desktop files, would be accessible in windows, which is not possible as it is now, because my ubuntu is on a ext4 file system.

So I wondered whether mounting a fat32 or ntfs partition as /home, would significantly decrease the speed of my system? I think it wouldn't because all the program files are still stored on ext4 systems.

Could anyone please comment on this?

---

### Post by dodle on 2011-09-19
I don't think it is a good idea to have a fat32/ntfs home partition because you can't set the permission flags. I don't know if it would even work. What you want to do is get Ext2fsd for Windows. It's a driver that allows Windows to mount Ext2/3/4 file systems. You can get it here: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by ibutho on 2011-09-19
I think you'd have problems running /home on an NTFS partitions. I don't think NTFS supports unix file permissions very well. One option you have is to mount /home on a linux partition, but have a shared ntfs partition as well, where you put the files you share with Windows.

---

### Post by garfieldpbj on 2011-09-19
> **dodle said:**
>  What you want to do is get Ext2fsd for Windows. It's a driver that allows Windows to mount Ext2/3/4 file systems. You can get it here: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)
Okay, I will try that...

---

### Post by garfieldpbj on 2011-09-19
> **ibutho said:**
> I think you'd have problems running /home on an NTFS partitions. I don't think NTFS supports unix file permissions very well. One option you have is to mount /home on a linux partition, but have a shared ntfs partition as well, where you put the files you share with Windows.

I was not aware of the permissions issues... I do have a "shared" ntfs partition (the one where windows is installed), but what I want is to have the data available without copying them first..

---

### Post by ibutho on 2011-09-19
What I meant was that you'd have your Windows partition, then a separate NTFS partition that you can access in both Windows and Linux. Sort of Like having C and D driving, but mounting D in both Windows and Linux.

---

### Post by ajgreeny on 2011-09-19
Not only is it not a good idea, but it is actually impossible to have /home on an ntfs partition, due as others have said, to the lack of linux permissions in ntfs.  If you tried it you would get lots of error messages at boot time.

I would recommend ibutho's idea of using a separate /data partition formatted as ntfs which will be available to windows without you doing anything at all, and can easily be made available to Ubuntu by using ntfs3g, (which is already installed by default), and ntfs-config, which you will need to install from software-center or using synaptic.

You can also have a separate /home partition on ext# format if you want, which will contain all your user configurations, emails, bookmarks and such things.  If you choose to go that route you will not need too much space for /home as no data files will be in there, so probably about 3 or 4 GB max, but I don't really know how much space that takes.   A separate /home makes life much simpler when and if you ever need to re-install or do a clean install of the next version of Ubuntu, and is strongly recommended in most situations, but slightly less important if you keep all your data separate.

---

