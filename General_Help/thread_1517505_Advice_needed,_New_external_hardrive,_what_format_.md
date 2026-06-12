---
title: "Advice needed, New external hardrive, what format ntfs or ext3 or4"
date: 2010-06-25
forum: General Help
---

### Post by dazndom on 2010-06-25
hi all,
 i have been searching forums and goofgle !! and any info i find is several years old, so please excuse me in advance.

i have new WD Mybook 1Tb and want to use it for file storage ONLY. 
Mostly music, video, photos, 

I have 5 boot system Vista, 7, ubuntu9.04 and lynx, slackware and am trying other linux flavors in future. !!!!
kids computers run xp, vista, 7 (bloody schools laptops)
and i want to join them all on home network and use the 1TB as the place everyone goes to get music or videos etc

I NEED some ADVICE on which format  to use for file storage NTFS, ext3/4 or something else !!!!
or should i partition drive 2,3,4 times

im leaning to ntfs but i HATE bill G with a passion, bloody virus infected ho, give me herpes anyday   :lolflag:

please any advice on setup  is greatly MUCHLY appreciated

cheers
Daz    :guitar:

---

### Post by VH-BIL on 2010-06-25
EXT4 seems to be a lot faster, especially when doing a disk check. But I don't know if there is an EXT4 driver for windows. The last time I mounted a Linux file system in Windows was back when EXT2 was the main file system and the driver worked well. If you can not find one and you need to access the drive in Windows then the only option is to use either EXT2 (maybe EXT3 if a driver is available) or a Windows file system such as NTFS or a FAT one.

---

### Post by kalistona on 2010-06-25
well a little confusion !
music, video  it is a thing and a machine is another thing.
best way is to buy a diskstorage[COLOR=Blue] multimedia[/COLOR].

ntfs ? fat ? ext3 or 4, well it is only a way to access your files...
see on the site 'diskstorage multimedia' and you will know that professionnal do and what is the format of their disks.

i, i should take ext4 ([COLOR=Blue] reiser[/COLOR] is a new modern format, almost finish...) and [COLOR=Blue]sony[/COLOR] is famous in this area...

---

### Post by Leppie on 2010-06-25
i presume you're going to connect the drive to the machine with 5 systems, including windows. windows only supports windows filesystems natively, so if you want to be able to access those files while in windows as well you will have to choose ntfs.
for network access, it really doesn't matter what filesystem you use as the clients access through samba or nfs or whatever you prefer.

---

### Post by justleen on 2010-06-25
If you need to share the data between windows/linux, i'd stick with NTFS. 

You could use[ ext2ifs]("http://www.fs-driver.org/") for ext2/ext3 under windows, but I have problems with  windows 7 and that driver (Need to reinstall the driver everytime windows boots..)

---

### Post by aeiah on 2010-06-25
if they'll be accessing it via a network i suggest ext4. its better at handling fragmentation, disk checking etc, and will play nicely with the linux server for backups and user permissions. ntfs *probably* will too, but why bother if you can go with something native?

if you'll be plugging it into different computers all the time, then i guess you'll have to go with NTFS. just make sure you remove it properly from linux machines or you may have to deal with a locked filesystem.

---

### Post by Leppie on 2010-06-25
-

---

### Post by warfacegod on 2010-06-25
> just make sure you remove it properly from linux machines or you may have to deal with a locked filesystem.

This is even more critical when it's plugged into a Windows machine.

---

### Post by dazndom on 2010-06-25
YEs external hardrive is plugged into my computer and i run UBUNUT 90% of the time.
vista is used for itune/ipods the kids have. 7 is new and im learning it for my IT course.
i download ALL music/video from itunes , p2p or ubuntu music store, etc, coz letting the kids use limewire or vuze has introduce virus/trojans 4 times so far this year and im sick of the hassle of scrubbing the laptops and reinstalling and putting everything back.

i would prefer to use ext4 and samba etc

WHAT is a locked file system, if drive removed incorrectly, how do i fixit if it happens

is ntfs worth ):P the hassle

---

### Post by warfacegod on 2010-06-25
You plug it into a machine that has the OS you didn't remove it properly from in the first place and then do so.

---

### Post by Leppie on 2010-06-25
> **dazndom said:**
> is ntfs worth ):P the hassle
depends if you want the data on that drive to be available when *you* are actually using windows.

---

### Post by dazndom on 2010-06-25
FIXED !!!
decided to partiton hardrive 
NTFS 100GB
ext4 900 GB

thanks to every one who gave me some advice/ help

cheersdaz

---

