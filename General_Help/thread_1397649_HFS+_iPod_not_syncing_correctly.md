---
title: "HFS+ iPod not syncing correctly"
date: 2010-02-03
forum: General Help
---

### Post by Platypus123 on 2010-02-03
Sorry as this seems to have been posted to death, but I'm having a variation of this common problem.

Being tired of my FAT32 partitions on my 80GB Classic, I had it reformatted on a Macintosh to HFS+ (Mac-formatted) at the Apple Store.  As per the abundance of threads online, I also had them disable journaling through the Mac's Disk Utility and it appeared it was ready for Ubuntu.  I added the UUID to fstab to allow write privileges.  Due to the issues I heard with getting it to mount in Banshee on 64-bit Karmic Koala, I used the killall -9 nautilus command and successfully got Banshee to read and mount the iPod.  After syncing my iPod, I verified that the content successfully transferred as the disk was now showing a large portion of the drive in use (presumably from the new media).  After disconnecting my iPod, from both Banshee and from Nautilus, the iPod presumably safely unmounts and disconnects giving me the okay to unplug it.  Whether I unplug it or not, after the OK to Disconnect progress bar completes, the iPod freezes (showing the silver Apple logo).  After a while, it seems to turn itself back on, but doesn't show any media on the device.  In fact, when I select 'About', it shows 0GB used and 0GB free (strange!). 

I've been to the Apple Store about three times to have them reformat it and start over as I keep thinking I'm doing something wrong along the way.  The data seems to be ON the iPod as I can play it back through Banshee (and on GTKpod), but the iPod menu itself doesn't seem to recognize anything and I can't access the music through the iPod.  I think the iPod database may be corrupted, but I don't understand why this is not corrected with a full restore and why I seem to be able to access the music through Ubuntu.

Does something immediately jump out at someone?  What am I doing wrong?  I'd like to get this fixed and I know there's a solution somewhere.

(P.s. I do NOT want to have to go back to a Windows-formatted, FAT32, iPod.)

(P.p.s.  I changed the permissions to my user rather than the 99 or something it was before.  Also, whenever I load the iPod in Banshee, it shows all the songs on the iPod.)

---

### Post by Platypus123 on 2010-02-06
*Bump*

Anything?

---

