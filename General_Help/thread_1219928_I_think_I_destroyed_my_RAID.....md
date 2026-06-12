---
title: "I think I destroyed my RAID...."
date: 2009-07-22
forum: General Help
---

### Post by ChampAmp on 2009-07-22
Last Night's Events:
1. Upgraded from 8.04 to 9.04

2. The upgrade cleansed my mdadm.conf (apparently a known bug that I found out about later).

3. I figured out that I would need to simply rebuild my mdadm.conf...and did so with mdadm command that outputs new mdadm.conf (can't recall it right now). Never again: It reconstructed as a RAID 0 (combined my two drives) instead of RAID 1...but I didn't know that until it was way too late.

4. Restarted....glad to see md0 was back...but no data.

5. Ran fsck....lots of blocks to relocate.....but it finished.

6. Ran tune2fs....cause I had no journal.....

7. All I have left out of 30gb of photos is a 7.5 gb lost + found folder with crap inside of it.

8. I know how to put the array back into a RAID 1 configuration now....but I'll probably have to format it, etc because it can only use one drive....the other reports no superblock, and dmesg | tail reports that the one it did use has a bad superblock....

9. Pretty sure I'm screwed, but if anyone thinks otherwise, please chime in. Thanks.....the lessons we learn best are those we learn the hard way. I hate myself.

---

### Post by Cheesemill on 2009-07-22
Your best option is to rebuild the RAID from scratch and then just restore the data from your backup.

I've said it before and I'll say it again.
RAID only provides business continuity in event of a drive failure. It is not a substitute for backups.

---

### Post by ChampAmp on 2009-07-22
Backup = A scattering of photos across 3 PCs, and, at this point, very incomplete. I need a practical backup for home, burning DVDs ain't it....and I don't want to invest in tape. Maybe I'll subscribe to someone's online backup service.

So while I agree with you, practical backups are easier said than done at home.

---

### Post by HereInOz on 2009-07-22
Cheesemill, is it still the case with Karmic Koala that you are unable to boot from one disk of a RAID1 array when the other disc has failed? (shutdown the computer, remove sdb, reboot - no joy). 

This has been an ongoing issue with Ubuntu for some time, and I am wondering if it has been fixed.

---

### Post by Cheesemill on 2009-07-22
> **HereInOz said:**
> Cheesemill, is it still the case with Karmic Koala that you are unable to boot from one disk of a RAID1 array when the other disc has failed? (shutdown the computer, remove sdb, reboot - no joy). 

This has been an ongoing issue with Ubuntu for some time, and I am wondering if it has been fixed.

I've no idea. I've never used software RAID1.

---

### Post by HereInOz on 2009-07-22
No worries, thanks.

---

