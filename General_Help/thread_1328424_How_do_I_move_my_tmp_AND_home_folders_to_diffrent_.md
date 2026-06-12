---
title: "How do I move my /tmp AND /home folders to diffrent hard drives?"
date: 2009-11-16
forum: General Help
---

### Post by TheOnlyMrK on 2009-11-16
Well the title says most of it, I have Windows 7 and Ubuntu 9.10 in a dual boot and I have Windows setup to use the "System" hard drive for (obviously) the operating system, the "Temp" drive for it's pagefile, temp folder, game caches, etc, and the "Media" drive for my music, movies, and so on.
So now that I'm getting more used to Ubuntu (and possibly deleting Windows from my computer since I never use it anymore and don't want to worry about hacking it to keep Windows 7) I want to set it up similar by moving /tmp to the Temp drive in a folder named "Ubuntu Temp" (/media/sdc1/Ubuntu Temp) and move my /home to a folder named "Ubuntu Home" in my Media drive (/media/sdb1/Ubuntu Home).
I have a feeling it's not too hard to do but I can't find any good or up-to-date help from searching Google. Here is my fstab if it is any help, all drives are only one partition except the System drive;

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  defaults                  0  0  
# / was on /dev/sda2 during installation
UUID=74ad2f75-0266-4ebb-a2ed-5810e741b707  /               ext4  errors=remount-ro         0  1  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sdb1     ntfs  nls=iso8859-1,umask=000   0  0  
/dev/sdc1                                  /media/sdc1     ntfs  nls=iso8859-1,umask=000   0  0  
```

---

### Post by Giblet5 on 2009-11-16
You cannot store linux files on an NTFS filesystem, and still use them under linux.

NTFS understands about one-third of all **_required_** linux file permissions, ownerships, and timestamps.

(FAT32 is even worse - it doesn't understand anything)

It. Will. Not. Work. Don't even try it.


That said, it's your system. Don't complain when it all stops working.

---

### Post by shaggy999 on 2009-11-16
Yeah, that won't really work. What you would need to do is create TWO new partitions on this drive formatted as some kind of linux file system (ext2/3/4, reiser, xfs, etc) and have one partition mounted to /tmp and the other to /home.

The best you could do would be to change the folders to soft links, but... ugh, that would really start to screw things up as mentioned above because of permissions problems and things.

---

### Post by searchfgold6789 on 2009-11-16
Get the GGnome partition editor from the Ubuntu Software Center. It will let you move different patitions around, as well as erase them. Be careful when doing this kind of thing, though. You should also use the system > administration disk utility to make disks bootable and whatnot. Keep track of the hard disks in BIOS so that you know which ones to boot from, what it will boot from, etc.

---

### Post by searchfgold6789 on 2009-11-16
> **searchfgold6789 said:**
> Get the GGnome partition editor from the Ubuntu Software Center. It will let you move different patitions around, as well as erase them. Be careful when doing this kind of thing, though. You should also use the system > administration disk utility to make disks bootable and whatnot. Keep track of the hard disks in BIOS so that you know which ones to boot from, what it will boot from, etc.
You should probably keep your system as it is though because ubuntu won't even recognize your games. It will recognize your documents though.

---

### Post by Giblet5 on 2009-11-16
> **searchfgold6789 said:**
> Get the GGnome partition editor from the Ubuntu Software Center. It will let you move different patitions around, as well as erase them. Be careful when doing this kind of thing, though. You should also use the system > administration disk utility to make disks bootable and whatnot. Keep track of the hard disks in BIOS so that you know which ones to boot from, what it will boot from, etc.

That's a very good idea, but DO A BACKUP FIRST.

A powerfail during a partition resize, as far as I am aware, has never ended without tears.

---

### Post by TheOnlyMrK on 2009-11-16
> **shaggy999 said:**
> Yeah, that won't really work. What you would need to do is create TWO new partitions on this drive formatted as some kind of linux file system (ext2/3/4, reiser, xfs, etc) and have one partition mounted to /tmp and the other to /home.

The best you could do would be to change the folders to soft links, but... ugh, that would really start to screw things up as mentioned above because of permissions problems and things.
Well the Temp drive is almost 80GiB so their is plenty of room to split it in half since I don't think either Windows or Ubuntu would ever need 40GiB for temporary files. So I'll just partition it in half and format the second partition as ext4. But still how do I move the /tmp folder? The /home I'll worry about more once I get the /tmp moved properly.

---

### Post by TheOnlyMrK on 2009-11-18
Well I think I'm just going to wipe my System and Temp drive and install nothing but Ubuntu 9.10 then set the certain spots to put the /tmp and /home folders, seems like that will be the easiest way and it will also get rid of Windows (Yaaay I'm finally no longer dependent on Windows!). I'll have to find another spot to move everything on my Media drive (almost 213GiB of files) so I can reformat it to a Linux filesystem. Would be nice if you could change a filesystem without erasing everything on it because I currently don't have the space to store 213GiB of stuff unless I MIGHT be able to split it all between my 150GiB System drive and 80GiB Temp drive as long as their not too filled up.
Does any one recommend a certain filesystem for my Media drive? It will mainly hold 5+MiB songs, 700+MiB movies/TV shows, and a few thousand pictures of various sizes, it won't be used for anything else but MY files, no system files or anything, should I just use the default ext4, use ext2, stick with NTFS, or what?

---

### Post by shaggy999 on 2009-11-20
> **TheOnlyMrK said:**
> Well I think I'm just going to wipe my System and Temp drive and install nothing but Ubuntu 9.10 then set the certain spots to put the /tmp and /home folders, seems like that will be the easiest way and it will also get rid of Windows (Yaaay I'm finally no longer dependent on Windows!). I'll have to find another spot to move everything on my Media drive (almost 213GiB of files) so I can reformat it to a Linux filesystem. Would be nice if you could change a filesystem without erasing everything on it because I currently don't have the space to store 213GiB of stuff unless I MIGHT be able to split it all between my 150GiB System drive and 80GiB Temp drive as long as their not too filled up.
Does any one recommend a certain filesystem for my Media drive? It will mainly hold 5+MiB songs, 700+MiB movies/TV shows, and a few thousand pictures of various sizes, it won't be used for anything else but MY files, no system files or anything, should I just use the default ext4, use ext2, stick with NTFS, or what?

Of all the current stable filesystems ext4 appears to be the best in most situations, with xfs topping out in some other categories. This article may be of interest to you:

[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

You might also want to look into using lvm2: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

Takes a little more setup, but pays off in the end.

---

### Post by lavinog on 2009-11-20
I don't see a good reason for moving /tmp.
I would also leave /home where it is too, and create a link to the other drive.
For instance I have /home/user and /storage/user
I store my pictures in /storage/user/pictures and have a symlink to it in my /home/user/pictures folder.  I have the same thing for videos and ISO files.
This lets me keep my home partition relatively small and managable.

---

### Post by TheOnlyMrK on 2009-11-20
> **lavinog said:**
> I don't see a good reason for moving /tmp.
I would also leave /home where it is too, and create a link to the other drive.
For instance I have /home/user and /storage/user
I store my pictures in /storage/user/pictures and have a symlink to it in my /home/user/pictures folder.  I have the same thing for videos and ISO files.
This lets me keep my home partition relatively small and managable.
Well I move the /tmp to improve performance and not waste space on the drive that I want only the operating system on, and I move the /home for both the same reasons and so I know my stuff is safe incase I mess something up and have to reinstall, which since I'm still new-ish to Ubuntu their is a good chance I'll break something at some point in time. If I used a swap space I'd put it on the same drive that /tmp is but I have 5GiB of RAM (can only use 3.2GiB thanks to 32bit) so don't need it since I don't do any heavy computer work.

---

### Post by lavinog on 2009-11-20
> **TheOnlyMrK said:**
> Well I move the /tmp to improve performance and not waste space on the drive that I want only the operating system on, and I move the /home for both the same reasons and so I know my stuff is safe incase I mess something up and have to reinstall, which since I'm still new-ish to Ubuntu their is a good chance I'll break something at some point in time. If I used a swap space I'd put it on the same drive that /tmp is but I have 5GiB of RAM (can only use 3.2GiB thanks to 32bit) so don't need it since I don't do any heavy computer work.

I do not believe that there will be any performance gains by moving /tmp.
My /tmp only takes up 88k and rarely gets to be larger than 200M at any given moment...it also gets purged during startup.

I have a second drive that I use just to mirror my files to using rsync.  What if your second drive failed...at least if your stuff was on both drives you wouldn't be lost.

---

### Post by TheOnlyMrK on 2009-11-20
> **lavinog said:**
> I do not believe that there will be any performance gains by moving /tmp.
My /tmp only takes up 88k and rarely gets to be larger than 200M at any given moment...it also gets purged during startup.

I have a second drive that I use just to mirror my files to using rsync.  What if your second drive failed...at least if your stuff was on both drives you wouldn't be lost.
If I'm not mistaken, the /tmp folder is heavily used during installs and updates, so it will significantly decrease install times because the head on the disk wouldn't have to constantly move to read one spot on the disk and move back to write to another spot, and I do care about my media files, but none of it isn't already backed up to the internet or worth a severe loss of performance just to make sure I have a "on site" back-up. Either way I only have one 1TiB drive, the second biggest I have is 150GiB and that's needed for the operating system plus I have near 250GiB of stuff.

---

### Post by TheOnlyMrK on 2009-11-20
> **shaggy999 said:**
> Of all the current stable filesystems ext4 appears to be the best in most situations, with xfs topping out in some other categories. This article may be of interest to you:

[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

You might also want to look into using lvm2: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

Takes a little more setup, but pays off in the end.
Thanks for the links, they helped a lot. After looking through that I'm going to stick with ext4.

---

### Post by dcstar on 2009-11-21
> **TheOnlyMrK said:**
> If I'm not mistaken, the /tmp folder is heavily used during installs and updates, so it will significantly decrease install times because the head on the disk wouldn't have to constantly move to read one spot on the disk and move back to write to another spot


Maybe, but installs and updates are trivial intermittent events and moving /tmp just to speed those up by a small amount is hardly worth it.

If you are really concerned about /tmp access time then make it a small RAM drive (as is done in Netbook installs).

---

### Post by TheOnlyMrK on 2009-11-21
> **dcstar said:**
> Maybe, but installs and updates are trivial intermittent events and moving /tmp just to speed those up by a small amount is hardly worth it.

If you are really concerned about /tmp access time then make it a small RAM drive (as is done in Netbook installs).
Yeah but the drive I call my "Temp" drive is nothing but an old 80GiB 7.2k RPM IDE drive that has nothing better to do and it's not like it's taking up valuable space in my computer either. So basically, the improvement may be small but it's better then a default install.

---

