---
title: "building a nas, need help with disk and data management"
date: 2011-07-17
forum: General Help
---

### Post by frente69 on 2011-07-17
Hi,
I currently have a 2TB qnap nas which will be relegated to mirroring important files from my new nas.
I am building up a HP Microserver with 2*2TB and want to look at the best way to manage the data, disks and backups.
My wish list:
[LIST]
[*] Power down unused drives
[*] I want all the disks to appear as one. 
[*] I want to be able to easily add an extra drive and add to the available space
[*] I want to be able to replace a disk with a larger one and add to the available space (It's ok if I have to manually copy the data from the old drive to the new drive)
[*] If a disk dies I want the remaining disks to still function with whatever data they have left on them.
[*] Email me if a drive dies
[*] If the server blows up then I can plug any drive from the server into another pc and copy the available data off the disk
[/LIST]

What would you suggest?

mhddfs - anyone use this much? What's the speed like? Do individual drives get spun down if not used? How is it decided which drive gets the data? No one talks about mhddfs much. It all seems to be about mdadm and raid and LVM which I don't think is suitable for my current purpose.

I have a existing qnap nas with a total of 2tb that will rsync changed files from the server nightly. To restore missing files would I use rsync in reverse?

---

### Post by tgalati4 on 2011-07-18
I like [http://freenas.org](http://freenas.org).  For your last requirement, you would need to set up the drives as JBOD (Just a Bunch of Drives) because any RAID configuration will be troublesome to remove a drive and try to extract data from it outside of the defined array.

I'm not familiar with mhddfs, but freenas runs ZFS pretty well, and it has some interesting data integrity features.

I'm not aware of any drive framework that will meet all of your requirements.  Some of them are mutually exclusive.

---

### Post by frente69 on 2011-07-18
I had a look at freenas but it seems to have taken to catering to enterprise type needs rather then home usage.

I'm really hoping to do this in Ubuntu otherwise I think unRAID([http://lime-technology.com/](http://lime-technology.com/)) fits the bill. I really like the idea that you can lose a drive without losing data, you can lose two drives and only lose the data stored on that drive, all the drives can be any size, any speed, any type. It just seems really flexible. 

Why can't unRAID be an app for Linux rather then it's own self contained server without any of the cool stuff like apt :-(

---

### Post by Zebediah49 on 2011-07-18
Agreed about freenas probably being a good choice.

Also agreed about ZFS being win for this.  However, even that will not let you have everything.  There is no system which will magically use the space on all the disks, allow arbitrary resizing, and support proper redundancy.

If you don't care about the redundancy, you can stripe together whatever you want, and it'll get bigger as appropriate.  Once you start asking for redundancy however, that gets tricky.  Personally I'd advise something along the lines of a raidz (zfs raid5), of the size you want.  When you want larger, you can upgrade the size, as long as you do all the disks simultaneously (you don't get the extra space until all disks are larger).

It actually sounds like you might just want them "strung together" though.  For read purposes, that's plenty easy: just use something like aufs to mount all of the disks on the same place, and it'll show up as a merge of them all.  I had a system composed of a mess of external disks (1TB, 500GB, 320GB, all USB) that worked like that.  You have to pick what disk to write to when you do writes (by writing to that disk, as opposed to the full set), but I think you can deal with that?

Note that I got rid of that system in favor of a proper raidz, which I recommend much more.  It's far nicer having a system that doesn't care about petty things like "unplugging a disk".

I would suggest you read up on how RAID systems work.  Some of your points (get what data is on a disk off) does not work with the way stripes are implemented, so you have to decide if you want to have the disks working "together" at the filesystem level or not.

If you do find a "file-level stripe" utility, I would be interested though.  I considered writing one a little while back, but never got around to it though.
(Idea: distributed DB of what disks have what; FUSE-based FS delegates reads and writes such that entire files are put wherever they should go.  Important files get higher importance values which results in getting placed in more places.  FS also balances load such that multiple operations use as many different disks as possible.)

---

### Post by frente69 on 2011-07-18
Thanks for the info. I have been doing a bit more research and I think I have a winner: FlexRaid
Rather then HDD based raid it is file based raid and can run either real time or in snapshot mode (I guess at timed intervals during the day). It sit's on top of the file system(not under it like normal raid) so your drives can be any speed and size etc, You can pick which files/folders/disks are synced and parity doesn't even need to live on the same server(helllloooo qnap nas). If a drive is removed you only lose the data stored on that drive.
Here is the wiki on it:
[http://en.wikipedia.org/wiki/FlexRAID](http://en.wikipedia.org/wiki/FlexRAID)

Here is a guide for running it on Ubuntu:
[http://www.havetheknowhow.com/Configure-the-server/Install-FlexRAID.html](http://www.havetheknowhow.com/Configure-the-server/Install-FlexRAID.html)

This sounds almost exactly like what I want.

PS Why is ZFS better then EXT4? Last I read ZFS wasn't classed as production on linux distros, only on some Unix distros.

---

