---
title: "Ntfs R/w."
date: 2006-03-10
forum: General Help
---

### Post by warpen on 2006-03-10
Hi,

this is my first post here...really helpful and interesting forums :)

I was wondering if I could in some way use my mounted NTFS-disk as a read/write disk? I have talked to a friend who says it's kind of tricky to make NTFS R/W when it's mounted, if not impossible, but I thought I should ask here first. He suggested that i put the following in my fstab:

```
/dev/hda1	/mnt/windows	ntfs	defaults,uid=1000,rw	0	0
```

...where "rw" is supposed to fix the read/write problem. But it doesn't work.

Anyone got an idea? :-k

---

### Post by astyanax on 2006-03-10
I was looking for this for awhile too and I asked some of my friends that are big Linux users.  They all said you can, but do it at your own risk, because they said that none of the packages that do it have been marked as stable yet.  There is a package called captive that will allow you to mount the partition with r/w access.  Here is the wiki:  [http://wiki.vidalinux.com/index.php/How_to_Mount_Windows_Partitions]("http://wiki.vidalinux.com/index.php/How_to_Mount_Windows_Partitions")

What I did was I just moved all my data over to other sources and repartitioned the NTFS drive as a FAT32 and copied the data back.  I wasn't willing to take the risk.

---

### Post by DOtSlaSHuCantCME on 2006-03-10
[QUOTE=warpen]Hi,

this is my first post here...really helpful and interesting forums :)

I was wondering if I could in some way use my mounted NTFS-disk as a read/write disk? I have talked to a friend who says it's kind of tricky to make NTFS R/W when it's mounted, if not impossible, but I thought I should ask here first. He suggested that i put the following in my fstab:

```
/dev/hda1	/mnt/windows	ntfs	defaults,uid=1000,rw	0	0
```

...where "rw" is supposed to fix the read/write problem. But it doesn't work.

Anyone got an idea? :-k[/QUOTE]

Try this Link  [http://wiki.serios.net/wiki/Accessing_NTFS_and_FAT_filesystems](http://wiki.serios.net/wiki/Accessing_NTFS_and_FAT_filesystems)

Also type "man mount" in terminal ,it has some cool mount options (like umask), 


with umask option your fat32 partitions becomes r/w with no headaches.
I believe they are issues with writing to ntfs,when i installed ubuntu i had
windows on a ntfs drive ......;) to make a long story short,i could not play,listen,move any of my goodies(mp3,movies data) that were on the windows side(partition),so i partitioned my 80gigs drive(the one with windows on it)to 5gigs ntfs for windows,and 3 vfat partitions,then i moved my mp3s,data,movies to the vfat partitions amd problem solved,now with umask option in fstab all vfat partitions can be read by Ubuntu.

:-k  i dont believe umask can be used with ntfs filesystems.

---

### Post by RJMacReady on 2006-03-10
To mount my windows partition I did a: ```
mkdir /media/windows
mount /dev/hda1 /media/windows -t ntfs -o nls=utf8,umask=0222
```

I can copy files off it, but not sure if I can write to it, never had to. Just change /media/windows to wherever you want it mounted. :)

---

### Post by The Mekon on 2006-03-10
I too have gone the FAT32 route.  I have a seprate FAT32 partition where I place all data which I need to read and write to from both Ubuntu and Windows XP.

I Googled "NTFS Linux" and see that Paragon are selling a product which they claim makes R/W to and from NTFS partions possible but as I have an adversion to buying software when using Linux. I will stay as I am.

There is also a solution using Wine.

Brian

---

### Post by warpen on 2006-03-11
Thanks alot for the help.

It seems as FAT is the way to go, I'm not willing to risk using a package that hasn't been marked as stable.

But I have not the same problem as some of you guys, I can copy files from my NTFS-disk *and* execute files. I think that this is enabled because of the ```
uid=1000
``` in my fstab. Not sure though, maybe it can help some of you.

---

### Post by syg00 on 2006-03-11
Below 2.6.15 do ***_NOT_*** attempt to use write for NTFS using kernel support.
Captive might be o.k. with fuse.

How valuable is that NTFS partition - _all_ (and any) of it ???.
I last tested at 2.6.13 when the (then) latest round of support was supposed to be stable(-ish). Not usable IMHO.
At some point I'll test .15 and/or .16 - the ntfsprogs folks do great work, but if you value your data be carefull.

---

