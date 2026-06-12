---
title: "Corrupt large files on software raid (ubuntu 8.10+)"
date: 2010-01-16
forum: General Help
---

### Post by innovate2000 on 2010-01-16
Hello all,
I am having a couple of RAID5 issues that are driving me mad. I have use an Ubuntu Box as a NAS for storing backups and as DVR storage. I have read that sometimes the RAM can be the issue - so I've checked that and there's plenty (4GB DDR2). The hard drives are 10 Western Digital 1TB drives (8TB available). This is realy not that germane because it this happens on all of my NAS boxes - I have two others: one with 8 x 500GB PATA drives and one with 8 x 500GB SATA drives. These issues appear on all of the servers. I've had this issue since 8.10 (currently using 9.10). The filesystems are all ext4 (but it happened in ext3 as well - which is why I went to ext4 - *hoping* that perhaps it might have been resolved - it hasn't.

Issue 1: My video files are playing *ok* (only *ok*) - it looks like there is some sort of congestion - apparently the drives are not reading the data fast enough to completely send the data over the wire to the client. (the video looks choppy and sometimes the image looks blurry and then catches up for a few seconds). Granted, the size of the files are huge (from 500MB up to 7GB), but if the data exists, what might be the cause for this?
Issue 2 (and the SIGNIFICANTLY more important issue): My backup files are not validating and therefore not restoring properly. I tried to do some research on the Ubuntu raid to see if perhaps I should not be using Software RAID for backup files, but I find nothing that tells me that I should not. The developer of the software I use (Image for Windows/Linux) to do the backups tells me that software raid is not supported (but hardware raid is supported) - but wont tell me why. I really do not wish to purchase raid cards and rebuild my raid devices (especially since from what I've read, the software raid should be able to do the trick). I've done a backup with Comodo backup (to the NAS box) and it *says* it verified OK - but the backups take 3-4 times as long to complete. So I'd obviously like to use something that works well and fast. I've even done the backup to an external (single) drive (enclosure), verified it (verifies OK), copied it to the NAS, copied it back to the external single drive(enclosure), tried to verify it again, and it fails. I wouldn't mind having to do this if I had to (the restore will not happen at all from the NAS - but will from an enclosure). I *REALLY* like using this software (Image for Windows) and have done so for years (primarily because they use something called PHYlock to do the backup even while I work on the computer - I think it takes a snapshot of the files, so any changes are lost, but I don't care about that).

Does anyone have ANY ideas? I really like the Ubuntu raid, but if it has significant limitations, then it really doesn't work for me.

Thanks

---

