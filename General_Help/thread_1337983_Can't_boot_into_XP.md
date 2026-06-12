---
title: "Can't boot into XP"
date: 2009-11-26
forum: General Help
---

### Post by racer13fly on 2009-11-26
Alright, so I have just fixed the major HDD problem I had earlier, and now I'm having some troubles booting up XP.  Whenever I boot up into GRUB, it just refreshes GRUB, nothing else happens.  Please help because I kind of need to get into XP soon.
Thanks

---

### Post by DapperMe17 on 2009-11-26
If you look at this thread ([http://ubuntuforums.org/showthread.php?t=1311782](http://ubuntuforums.org/showthread.php?t=1311782)), ranch hand provides a script that adds temporary access to your Ubuntu & Windows partitions.

On my dual boot, I had to add that script, just to "get" to XP.

It works, so give it a shot.

My Grub is still buggy, as I can still not arrow down past the second option listed in Grub. 

At the very least, you'll be able to get to either Ubuntu, or XP with the script.

I too, am hopeful that Grub2 is being "fine-tuned"

---

### Post by jacobs444 on 2009-11-26
Worse come to worse, you can load your XP CD and then select the repair(not automated system recovery) option, and run fixmbr, and then fixboot. 

!!!!!!!!!!!!!!!!!!!!!!!!!!Note that this will overwrite grub, and linux will not be bootable!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by racer13fly on 2009-11-26
Well I just booted the Super Grub Disk, and when I booted it, it made it so I can't boot normal GRUB at all, just shows a GRUB_ at the top and won't let me do anything.  I tried reinstalling GRUB with it, but it won't work, keeps telling me that there are files missing, both with Linux and the GRUB files that are on the disk.  I'll have to remake another disc I'll have to redownload it again and burn again I guess...

EDIT: Well I just looked around your links and I found that tutorial on reinstalling GRUB, and it work, thanks!  But I'm still having the same issue with XP...

---

