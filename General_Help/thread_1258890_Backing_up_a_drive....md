---
title: "Backing up a drive..."
date: 2009-09-05
forum: General Help
---

### Post by Gizenshya on 2009-09-05
I'm tired of reinstalling an entire OS and all the programs I want every time I screw something up (which is far too often... *ahem*).

So I want to make images of bootable drives/partitions so I can just recover and go about my merry way.

I've been googling for a while and a few rograms came up a lot as being helpful: ddrescue, testdisk, and partimage.

I've found lots of informationabout backing up drives, and restoring drives, but I can't figure out how to restore a bootable drive after recovery.

ATM, I'm dd'ing a drive that should be finished soon (an NTFS volume).  It has my XP and Ubuntu just how I like it (from wubi).  Now... once I get done making the image, assuming I have a formatted NTFS volume of sufficient size, what do I do?

one more thing.  I'm using liveCD's for recovery.  ATM backtrack 3 (just because it probably has all those type tools by default).  If it doesn't have one, I have about 10 other distros (latest stable versions).  I'm on 56k, so I'm stuck with live CD's since I can't download much now :(

*edit* ugh!!! just realized the drive I was backing it up to is FAT32 and I hit the 4gb limit.  I'll have to go grab another drive and start over :(

---

### Post by CrusaderAD on 2009-09-05
Norton Ghost works really well...

[http://www.symantec.com/norton/ghost]("http://www.symantec.com/norton/ghost")

---

### Post by starcraft.man on 2009-09-05
testdisk is for creating a new partition table after ya damage existing one. Partimage is a good drive image solution, nice ncurses gui in a terminal. ddrescue is a dd backup solution, I prefer partimage to be honest. Nothing wrong with dd though, not sure, does it offer any compression or just a raw copy? Without compression images can get large.

I'd recommend ya look at partimage for imaging the root system. Don't back up home, that should be backed up through other means. I wrote a good wiki on backup [here]("https://help.ubuntu.com/community/BackupYourSystem"). As to restoring grub after a reinstall, see [here]("https://help.ubuntu.com/community/GrubHowto"). Those two wikis and links to subpages should cover lots of good info.

Partimage can be done from any Ubuntu live CD, it is only 32bit though, so don't try installing on a 64 cd, it just won't work. Read through the wikis and formulate your own strategy, there are lots of backup means and its good to use a mix so as not to depend on just one thing. The key to backup is distributed redundancy.

Edit: Two notes, partimage also offers to backup and restore MBR btw, makes it easier, especially if its unchanged. 

As to raptormanad's suggestion, I see no reason to use a paid solution like that, and even less to support a useless company like Symantec. gparted is pretty straight forward, read screens, if you must, see partimage docs [here]("http://www.partimage.org/Partimage-manual_Usage").

---

### Post by CrusaderAD on 2009-09-05
> **starcraft.man said:**
> As to raptormanad's suggestion, I see no reason to use a paid solution like that, and even less to support a useless company like Symantec. gparted is pretty straight forward, read screens, if you must, see partimage docs [here]("http://www.partimage.org/Partimage-manual_Usage").

I completely agree here. It's good we got a great reply from starcraft man, thanks. Symantec is just crap in general but that was the only program I was aware of for this situation.

---

### Post by Gizenshya on 2009-09-05
well, I haven't checked if partimage is on any of the liveCD's.  If it isn't, I'm SOL as far as that goes.

The thing that is complicated here is that I want to backup the drive/partition byte-for-byte.  I don't want to just backup files, or have a separate mbr record backup.  I just want one file, where I can just say "program /dev/blank_NTFS_volume /dev/NTFSimage" and it does it's thing-- or as close to that as possible.

I would like to strip off the excess bytes (all several GB of them from a byte-for-byte copy to save space... but simplicity is paramount for me.  If I have to do files, settings, MBR, and everything separately, then it isn't for me.  I can backup files as needed, and I have ways of getting my settings backed up and restored, but I hate doing it.  But if partimage will compress and restore a complete drive byte-for-byte (easy-to-restore, lossless compression), then I'm game :)

Any idea which distros might have it on their liveCD? I have Knoppix, PCLinuxOS, Ubuntu 8.04-9.04, Debian, Backtrack 3 CD and 4 DVD, LinuxMint, DSL, ArchLinux, and several more that I can't think of off the top of my head.

I have some old DOS programs that came with hard drives back when hard drives came with such things, and they worked perfectly.  But they only copy from drive to drive, and have no images.  I want them as image files so I can put other things on the drive as well, and not just have a zillion hard drives that each have one thing on them.

There are also compatibility issues with the old software and drives now are just too big for them (and have been for some time... lol).

Thanks for the help so far :)

That image still isn't quite done... USB 1 is a pain lol

PS: in addition to what was mentioned above, I've had experience with Symantec's Norton Ghost and I've concluded it is absolute crap.  The old DOS programs worked far more reliably and were compatible with everything (under a certain size...).  I would backup drives thinking I was fine just to be burned time and time again.  It worked once.  Once out of a couple dozen tries.  From errors backing up (reported and not), to crashing, to incompatibility, to just not restoring even after saying everything went fine.  To be honest, everything I've ever tried from Symantec is crap.  Their software is not worthy to grace my computers.

---

### Post by starcraft.man on 2009-09-05
> **Gizenshya said:**
> well, I haven't checked if partimage is on any of the liveCD's.  If it isn't, I'm SOL as far as that goes.


It's in the universe repositories, not maintained by Ubuntu. See System > Admin > Software sources and check of universe. Alternatives see sig for more complete. Universe repositories = anything canonical doesn't maintain or isn't from standard Ubuntu/GNOME. It is a tiny download compared to other program, only has an ncurses gui in terminal, ya can manage it on even slowest connection compared to time takes for a backup. Easy to use.

> The thing that is complicated here is that I want to backup the drive/partition byte-for-byte.  I don't want to just backup files, or have a separate mbr record backup.  I just want one file, where I can just say "program /dev/blank_NTFS_volume /dev/NTFSimage" and it does it's thing-- or as close to that as possible. 
If you say so, I can only say that doing many whole drive back ups will quickly leave you running out of space. I do drive images of when I set up everything right, then keep incremental backups in an archive file of some sort, say tar.gz. Easy to restore, or use a folder sync.

> I would like to strip off the excess bytes (all several GB of them from a byte-for-byte copy to save space... but simplicity is paramount for me.  If I have to do files, settings, MBR, and everything separately, then it isn't for me.  I can backup files as needed, and I have ways of getting my settings backed up and restored, but I hate doing it.  But if partimage will compress and restore a complete drive byte-for-byte (easy-to-restore, lossless compression), then I'm game :)
It does. It's only limitation is the space your saving it to. It supports gzip compression by default (good enough for most), bzip2 also, but there is a bug with restoration of mbr. gzip is enough.


> Any idea which distros might have it on their liveCD? I have Knoppix, PCLinuxOS, Ubuntu 8.04-9.04, Debian, Backtrack 3 CD and 4 DVD, LinuxMint, DSL, ArchLinux, and several more that I can't think of off the top of my head.
Drive imaging isn't exactly a standard thing, I don't think any, except for rescue type cds. Like, [systemrescueCD]("http://www.sysresccd.org/Main_Page").

> I have some old DOS programs that came with hard drives back when hard drives came with such things, and they worked perfectly.  But they only copy from drive to drive, and have no images.  I want them as image files so I can put other things on the drive as well, and not just have a zillion hard drives that each have one thing on them.
In my experience, hard drives were never 'perfect'. There were always better and worse makes/models but nothing was ever perfect and lasted forever in my experience.

> 
There are also compatibility issues with the old software and drives now are just too big for them (and have been for some time... lol).

Thanks for the help so far :)

That image still isn't quite done... USB 1 is a pain lol
Your welcome. I guess I'm Mr. Backup. :)

Edit to your edit: I concur. In general, all Symantec software is crap. The biggest travesty, is they've bought over the years companies I actually liked. Take their firewall solution, they bought sygate a nice free wall for that. Ruined it entirely afterwards.

---

### Post by Gizenshya on 2009-09-05
I meant the old dos programs worked perfectly.  But, many of those old drives are still alive and kicking as well.  They at least seemed more reliable than current drives.  Could just be me, but it could also be them pushing the tech.

I see what you mean now... before I misunderstood.  And I suppose I do that anyway.  I'll get everything set up nice and do backup syncs as well.

After I posted that last time I looked at the tutorial you posted and it explains exactly what I wanted to know with ddrescue.  and some stuff I didn't know that I wish I would have before.  1.  how dangerous the program could be!  whew, I'll keep that in mind.  and 2.  the compression.  Is it too late to compress after it's done?  I mean, if I compress now, will I have to decompress it before I use it, or will ddrescue just go from what I guess would be a .img.gz file?  Or is is automatically compressed?  I just ask that because I think I saw something about adding gzip or something in the command line, but I didn't.

---

### Post by starcraft.man on 2009-09-05
> **Gizenshya said:**
> I meant the old dos programs worked perfectly.  But, many of those old drives are still alive and kicking as well.  They at least seemed more reliable than current drives.  Could just be me, but it could also be them pushing the tech.


I guess some drives with really high areal density are more prone to errors, but buying the right drive can go a long way. I stick to midsized drives.

> I see what you mean now... before I misunderstood.  And I suppose I do that anyway.  I'll get everything set up nice and do backup syncs as well. Good, backup is best ounce of prevention. Seen too many people crying about deleting X.

> After I posted that last time I looked at the tutorial you posted and it explains exactly what I wanted to know with ddrescue.  and some stuff I didn't know that I wish I would have before.  1.  how dangerous the program could be!  whew, I'll keep that in mind.  Very in my experience, one typo and poof. 

>  and 2.  the compression.  Is it too late to compress after it's done?  I mean, if I compress now, will I have to decompress it before I use it, or will ddrescue just go from what I guess would be a .img.gz file?  Or is is automatically compressed?  I just ask that because I think I saw something about adding gzip or something in the command line, but I didn't. You can compress independently after the dd image is created. This isn't ideal, since you'll have in the end created a large blob that is compressed after the fact. In future, you'd have to uncompress it before restoring, either in two steps or more advanced using a pipe | (uncompressing, then passing stout to dd for restoration, a bit advanced but not too hard). See the tar.gz section of my wiki for examples using a pipe and how works. You could have passed dd through a pipe to compress on the fly (i.e. as each byte is backed), dd itself doesn't do compression on it's own. It's a legacy UNIX command, a hold over, doesn't even conform to the standard GNU linux command structure, that takes some folks for a ringer.

Partimage handles this transparently and very well, though no support for EXT4 yet since it still new (it will backup, but it will do everything include freespace like dd then compress I believe, or perhaps not). It handles compressiong and uncompression, as well as backing and restoring only certain partitions. It's a good free solution. More than that, the clear GUI makes it very hard to do damage, unlike dd.

---

### Post by theozzlives on 2009-09-05
> **raptormanad said:**
> I completely agree here. It's good we got a great reply from starcraft man, thanks. Symantec is just crap in general but that was the only program I was aware of for this situation.

Norton wasn't always wishy washy. In the DOS days they had some very powerful utils like Disk Edit, old Disk Doctor, old Speed Disk (which Microsoft copied) and Unerase. I missed the Disk Editor when it went Windows.

---

### Post by starcraft.man on 2009-09-05
> **theozzlives said:**
> Norton wasn't always wishy washy. In the DOS days they had some very powerful utils like Disk Edit, old Disk Doctor, old Speed Disk (which Microsoft copied) and Unerase. I missed the Disk Editor when it went Windows.

My comments were all directed at everything recent they've ever made/ruined (last 10 plus years). Maybe back in the day half decent, but those times are long gone. Now, they just make bloat and push it on IT people who know nothing. Norton's become a trusted name in the same way CNN has, in name only, makes people feel secure. Once they got big enough, they stopped caring about quality like every other large corporation. Anyway, kinda off topic, I think that covers all questions from OP. Probably shouldn't get all started dogging on Norton...

---

### Post by Gizenshya on 2009-09-06
Unfortunately there is a snag...

when I entered:

```
dd if=(file) of=/dev/hda1
```

(well, the equivalent in my situation), it said it can't do that because /dev/hda1 is a directory.  I looked at the help and it said for the operand "of" it writes to a file instead of a stdout (whatever that is).  I thought... well, maybe try stdout=dir... didn't work.

/dev/hda1 is a blank NTFS volume which is larger than the image file. (20gb vs 16 gb).  So I don't see an issue with that.  I must be using the wrong operand or something. :(

any ideas?

can partimage work from a *.img file?

and regarding the OT discussion... very true.  Unfortunately it is even more wide-spread than that.  Blizzard for example.  They (be it through mergers or greed...) have lost all respect for their customers.  WOW is one thing... but with starcraft 2's lack of LAN play (requirement to be connected to servers to play with your buddies), drm issues, and spliting into multiple discs that are sold separately, I've lost all respect for them as well.  As much as I like much of their (Blizzard's) work up to around 2000.  I don't mean to single them out in gaming, however.  Bethesda Softworks is just as guilty (as much as I LOVED Morrowind and Oblivion), their intrusive use of DRM and forceful implementation of "*net framework" is unacceptable.  Nearly every maker has slapped their customers in the face.  Personally, I won't take it.  I would love to get fallout 3, Starcraft 2, Bioshock 2, Diablo 3, Gears of war (any), and many other recent games, but not with their practices.  They insult their customers by treating them like criminals, which pushes them (including myself) away.  Then they blame it on people stealing their software, and increase their insulting activities, which pushes more people away... when it is not the criminals' fault, it is the developers'.  And as a final stake in the heart of their illogical arguements, look at the people who do steal.  They crack everything and get a more enjoyable experience than the people who actually bought the game.  I'm done with playing such games until they improve their practices.  [/rant]

---

