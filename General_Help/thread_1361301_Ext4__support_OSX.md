---
title: "Ext4  support OSX"
date: 2009-12-21
forum: General Help
---

### Post by alexdotcomm on 2009-12-21
I use external drives between my mac and my many ubuntu systems. I didn't use FAT32 because of the 4 GB file size limit. The last driver that allowed OSX to read and write to Linux file systems was EXT2FS. It allowed mounting of Ext2 file systems, the project apparently has been abandoned since 2006. Since Ubuntu now comes with Ext4 it would be great to have an Ext4 driver for OSX, to use between systems. Even these days flash drives are getting bigger and they are still limited to 4 Gb files. In this day and age why did we not as yet come up with a file system to use between many operating systems. I think Ext4 would be a good choice.

---

### Post by juancarlospaco on 2009-12-21
*So...* 
Whats the problem with Ubuntu?, its reads EXT2, EXT3, EXT4, HFS, NTFS, FAT32, and more...
Send an email to OS X developers.

---

### Post by alexdotcomm on 2009-12-21
I know, and i do use Ubuntu to mount many different file systems, but it would be very rare for some OSX developer to want to give osx ext4 R/W. A driver for OSX for ext4 would more likely come from the Linux community than the OSX community. I use both OSX and Ubuntu but i do not have the know how to accomplish such a feat.

---

### Post by juancarlospaco on 2009-12-21
Try..., dont loose your hope, 
i dont know OS X developers, 
but if they are like Linux Developers, maybe you are lucky.
EXT4 is standard, documented, and Open Source, its not a unaccesible black box.

Anyways a OS X driver needs to be developed under OS X kernel and such.

or just use EXT2 if works for you, works perfect on Ubuntu.

---

### Post by alexdotcomm on 2009-12-21
Lets hope so i'll try posting it on an OSX dev Forum

---

### Post by lukeiamyourfather on 2009-12-21
Its unlikely that OS X will have support for ext4 soon, or ever. From my brief understanding of file systems, many features of ext4 make it much more difficult to implement than traditional file systems like FAT32 or ext2. Its a journaled file system which makes it more complex, it uses extents which make it even more complex, and if that's not difficult enough it now implements timestamps differently than most other file systems. All of the new features are good for the Linux user but make it less likely to be ported or adapted anywhere else. Other file systems are showing similar trends in that they are sacrificing portability and simplicity for robustness and performance.

If you need to share files between OS X and Linux that are larger than 4GB in size I'd suggest setting up a dedicated system for storage. Probably a system with Ubuntu and ext4, then share that with the OS X system using NFS or CIFS (Samba). That way the client doesn't care what file system is used because it just sees whatever share its given. Cheers!

---

### Post by alexdotcomm on 2009-12-21
Excellent idea i could use that, maybe even enable Jumbo Frames for quicker access across the network on Samba.

Thanks

---

### Post by k32 on 2010-08-23
guys, I think i found a solution, well at least i'm very close.

i have 3 machines here i my bedroom> a AMD phenom II x4 955-1.5 TB hd(NTFS), 250gb hd(Ext4), another 320gb hd(also Ext4)- running mint9 isadora x64. The other 2 machines are a sony vaio running mint8 x64, and a brand new snowy mac book.

 I finally figured out how to map all those shares on my local net. I followed [this]("http://blog.ibd.com/sysadmin/bonjour-avahi-netatalk-to-share-files-files-between-ubuntu-10-4-mac-os-x/") tutorial and now all the macs on my place R/W on all those fs's. Dunno how long the NTFS FS will last but so far so good. 

I've been trying to keep my bedroom a ms-free-area for the last 3 years \o/ :D !!!!

After spending twenty years of hope on MS I decided that I had to change... today I am a very proud "almost-advanced-user" that manage to build his own vpn with a little help from teamviewer and configuring my netatalk and avahi services on mint9. 

everything here working like a charm!!!

I hope you can find this link as much useful as i did!! 

best regards!

---

### Post by neglesaks on 2011-02-25
> **lukeiamyourfather said:**
> Its unlikely that OS X will have support for ext4 soon, or ever. From my brief understanding of file systems, many features of ext4 make it much more difficult to implement than traditional file systems like FAT32 or ext2. Its a journaled file system which makes it more complex, it uses extents which make it even more complex, and if that's not difficult enough it now implements timestamps differently than most other file systems. All of the new features are good for the Linux user but make it less likely to be ported or adapted anywhere else. Other file systems are showing similar trends in that they are sacrificing portability and simplicity for robustness and performance.


The Mac's HFS+ filesystem, while not as modern as the ext3/4 family, is also using a journal and an extents file, and as such about the same complexity to implement as what Apple already has in place.

But since Apple hasn't bothered implementing ext2 or ext3 support though those fs' have been open and available for years, don't expect ext4 support on that front. I'm guessing after the ZFS fiasco that Apple will rather implement btrfs (which is closer to the ZFS specs than ext4) into the OS X once they are openly willing to admit how antiquated HFS/+ is.

As for 3rd party developers, there is both paid-for software that allows ext2 and 3 support in the Mac (like [this]("http://www.macupdate.com/app/mac/33374/paragon-ext2-ext3-fs")), and a free extension, but I have yet to see an ext4 solution of either kind.

---

### Post by gerard.lledo on 2011-03-25
I have written a read-only implementation of ext4 that works on OSX using macfuse.  I know of some people using it on FreeBSD and it also works on linux, although that is probably not as useful :P.

[https://github.com/gerard/ext4fuse]("ext4fuse")

---

### Post by N00b-un-2 on 2012-05-11
Paragon has a driver for Ext2/3/4.
[  ]("http://www.paragon-software.com/home/extfs-mac/release.html")

it is not free software, and as of OSX 10.7+ "Lion" EXT4 is not supported but does still work on 10.6+ "Snow Leopard".  I've tried the MacFUSE modules and they do not work.  Not in any reasonable manner anyway.  I've been able to -force mount an EXT3 partition as EXT2 and the result was a kernel panic followed by a corrupted hard drive.  Don't bother trying to use the MacFUSE EXT module

---

### Post by idoitprone on 2012-05-12
> **N00b-un-2 said:**
> Paragon has a driver for Ext2/3/4.


it is not free software, and as of OSX 10.7+ "Lion" EXT4 is not supported but does still work on 10.6+ "Snow Leopard".  I've tried the MacFUSE modules and they do not work.  Not in any reasonable manner anyway.  I've been able to -force mount an EXT3 partition as EXT2 and the result was a kernel panic followed by a corrupted hard drive.  Don't bother trying to use the MacFUSE EXT module

A few things

Try not to revive old threads

MacFuse haven't been maintained for over 2 years

Use its successor OSXFuse
[http://osxfuse.github.com/](http://osxfuse.github.com/)
OP use ext3 or ext2 since it is miles better than htf+ in terms of keeping your data safe

---

### Post by coffeecat on 2012-05-12
The OP has not been back for several months. If anyone needs help with this or a related issue, please start a new thread. Old thread closed.

---

