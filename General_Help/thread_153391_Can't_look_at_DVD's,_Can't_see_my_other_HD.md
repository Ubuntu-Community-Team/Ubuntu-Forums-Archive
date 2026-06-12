---
title: "Can't look at DVD's, Can't see my other HD"
date: 2006-03-31
forum: General Help
---

### Post by Rebeca on 2006-03-31
I have two questions. They might be simple, but I'm new to ubuntu - and linux in general, so I would appreciate any help.

1. I have one cd/cdrw drive and the other is a cd/dvd drive. I don't have any problem trying to open or close these drives. I can also listen to cd's fine in both drives. However, when I want to watch DVD's (yep, using the cd/dvd drive), the CD/DVD creator opens - and when I try to use totem to watch the DVD, the option to Play disc DVD-Rom disc is greyed out. I already have libdvdcss2 and totem-xine. What else do I need to do?

2. I have two hard drives. I can see the main one which is the one where ubuntu is of course, however, I haven't been able to access the other one, which has a little bit of more space - which I do need. Did I miss something during installation? What do I have to do to use my other hard drive as well? When I try to open Disks Manager, it opens and it only keeps loading and loading....

If it helps, here's my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat rw,user,noauto  0       0


---

### Post by dcstar on 2006-03-31
[QUOTE=Rebeca]I have two questions. They might be simple, but I'm new to ubuntu - and linux in general, so I would appreciate any help.

1. I have one cd/cdrw drive and the other is a cd/dvd drive. I don't have any problem trying to open or close these drives. I can also listen to cd's fine in both drives. However, when I want to watch DVD's (yep, using the cd/dvd drive), the CD/DVD creator opens - and when I try to use totem to watch the DVD, the option to Play disc DVD-Rom disc is greyed out. I already have libdvdcss2 and totem-xine. What else do I need to do?

2. I have two hard drives. I can see the main one which is the one where ubuntu is of course, however, I haven't been able to access the other one, which has a little bit of more space - which I do need. Did I miss something during installation? What do I have to do to use my other hard drive as well? When I try to open Disks Manager, it opens and it only keeps loading and loading....

If it helps, here's my fstab:[/QUOTE]
Look in your /dev directory, there should be "dvd" links to your hdc and hdd devices, if not then that is the DVD issue.

As for your second hard drive, I assume it is a Slave IDE device on the first IDE channel?

---

### Post by trent dillman on 2006-03-31
1. Is your dvd drive cdrom 0 or 1?

2. Your hdb isn't in your fstab...

---

### Post by Rebeca on 2006-03-31
I only see one dvd link to my hdd device. Do I have to create one for my hdc device? If so, how do I do that?

As for my second HD, I'm not sure...

**Edit:**

> Is your dvd drive cdrom 0 or 1? It's 1.

---

### Post by Rebeca on 2006-04-01
I got some more information through Terminal, here:

> root@ubuntu:/home/[username] # fdisk -l /dev/hdb
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xfffff5f6 of partition table 5 will be corrected by w(rite)

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/hdb2            2434        4865    19535040    f  W95 Ext'd (LBA)
/dev/hdb5   ?      260347      250911  2071690107   f6  Unknown


That is the second HD I was talking about. And, I suppose that means I messed up somewhere since it seems my old windows stuff is still there? Blah.

So, I still need help with both things I mentioned at the beginning of this thread. Any ideas?


**Update:** I was able to solve the hard drive problem with the instructions given here: [https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions)

However, I still have problems trying to play a DVD. Please help?

---

### Post by dcstar on 2006-04-01
[QUOTE=Rebeca]
......
So, I still need help with both things I mentioned at the beginning of this thread. Any ideas?[/QUOTE]
Do:
```
sudo mkdir /c
sudo mkdir /d
```

Then add these lines to your fstab file:
```
/dev/hdb1       /c		vfat    	umask=000,noatime,auto			0       0
/dev/hdb2       /d		vfat    	umask=000,noatime,auto			0       0
```
Then:
```
sudo mount -a
```
That should mount your Windows partitions as "/c" and "/d".

As for your DVD, you may need to check System-Preferences-Removable Drives and Media and see what the Video DVD setting is.

---

### Post by Rebeca on 2006-04-01
It is set to "Play video DVD disks when inserted"
Command: totem %d

Do I have to change anything there?

---

### Post by Rebeca on 2006-04-01
Thank you for helping me before, dcstar.

I was finally able to play a DVD. I didn't change anything on my fstab, but I was able to mount the cdrom1 dvd by typing the following:

> sudo mount /media/cdrom1/ -o unhide

That way I was able to see the files inside cdrom1 when browsing it through Nautilus. I can play the DVD using mplayer (I have to open mplayer and select play DVD), but I haven't had any luck with totem yet. And, I still haven't figured out **how to make it play the DVD automatically** after I insert it. I have tried a bunch of ideas given in other threads, but nothing seems to work so far. If anyone knows what I should do, please tell me.

My current fstab looks like this:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 vfat rw,user,fmask=0111,dmask=0000 0 0


And as I mentioned before, I have totem-xine, totem, libdvdcss, w32codecs, and mplayer. The default behavior every time I insert a DVD is an icon that appears in my desktop, which will open the CD/DVD creator when double clicked. Any ideas will be appreciated.

---

### Post by Rebeca on 2006-04-02
OK. I still haven't figured out what I have to do to make this computer play DVD's automatically. Anyway, I recently encountered another problem: there's a DVD of The Beatles I can't seem to play in any of my dvd players (mplayer, gxine, etc). I'm not sure if it has anything to do with its format: 

NTSC
Picture Format: 4:3
Colour Mode: Black & White
Disc Format: DVD-9
Audio: Mono

What should I do?

---

### Post by dcstar on 2006-04-02
[QUOTE=Rebeca]It is set to "Play video DVD disks when inserted"
Command: totem %d

Do I have to change anything there?[/QUOTE]
Mine is:
```
totem dvd://
```

---

### Post by dcstar on 2006-04-02
[QUOTE=Rebeca]OK. I still haven't figured out what I have to do to make this computer play DVD's automatically. Anyway, I recently encountered another problem: there's a DVD of The Beatles I can't seem to play in any of my dvd players (mplayer, gxine, etc). I'm not sure if it has anything to do with its format: 

NTSC
Picture Format: 4:3
Colour Mode: Black & White
Disc Format: DVD-9
Audio: Mono

What should I do?[/QUOTE]
What Zone is the DVD? (and is your DVD drive locked to a different zone?)

---

### Post by Rebeca on 2006-04-09
I made the change to totem totem dvd:// instead of the %. At first, it seemed that nothing really happened, but after a restart, I was able to play the DVD. (I had also checked if there might have been a problem with the DVD zone, but everything was fine - I didn't have to make any changes.) So, I have no problems now. Thanks for all the help.

---

