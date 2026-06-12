---
title: "NTFS issue"
date: 2009-11-01
forum: General Help
---

### Post by zyxyellowxyz on 2009-11-01
I decided to post this question here because:
[LIST=1]
[*]Windows help sucks
[*]Ubuntu users know how to fix stuff
[*]All places I go say that the partition is crapped. This is wrong
[/LIST]
Ok, here's the skinny of it
I rebooted my computer this morning, to get into windows (Love playing Aion).  When it first started, it told me chkdsk needed to run, so I let it. It found some corruption on our big drive (we have 2 HDDs, one 360GB, and one 1.5TB), fixed them, and rebooted. It said it needed to do a chkdsk on the drive. I let it. No errors found. got into windows, and it said that the drive is corrupt.  I reboot into Ubuntu, and it see's the drive just fine. I run checks from Ubuntu, no errors. I open some videos on that drive. No problem.

I reboot into windows, it needs to do a chkdsk. No errors. Boots into windows, corrupt.  You see the loop?

Ok, while booted into windows, I  run chkdsk from cmd, as Administrator:
```
CHKDSK is verifying files (stage 1 of 3)...
  581568 file records processed.
File verification completed.
  19302 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
  657286 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  581568 file SDs/SIDs processed.
Security descriptor verification completed.
  37860 data files processed.
CHKDSK is verifying Usn Journal...
  17842096 USN bytes processed.
Usn Journal verification completed.
Windows has checked the file system and found no problems.

1157937151 KB total disk space.
 359021036 KB in 522199 files.
    103396 KB in 37861 indexes.
         0 KB in bad sectors.
    793587 KB in use by the system.
     65536 KB occupied by the log file.
 798019132 KB available on disk.

      4096 bytes in each allocation unit.
 289484287 total allocation units on disk.
 199504783 allocation units available on disk.
```
Everything seems OK. Next, I go into computer manager, by right-clicking on "Computer" from the Start menu. I look at the drive from there, and it says 
```
(X:)
1104.29 GB RAW
Healthy (Primary Partition)

```
It doesn't even see that it's NTFS, even though chkdsk does.  Ubuntu sees it as NTFS, and can even read/write to it -- no problem. Any ideas on what to do next?

---

### Post by Bjalf on 2009-11-01
This is what I would do:

1. Backup.
2. Get better hard drive tools, or just reformat.
3. Restore backup if neccessary.

I would not:
-skip backup
-involve geek squad

---

### Post by seeker5528 on 2009-11-02
Backup is definitely suggested before doing anything that might risk the data any further.

The options I can think of off the top of my head.

Install testdisk, unmount all the partition on the disk in question, run testdisk to scan for partitions on the disk, then have testdisk write the partition data. If the partition in question is not the only partition on the disk, there is always some chance that this could affect data on the other partitions.

Try to use gparted to shrink the partition, re-boot into windows so windows will check the disk, if it doesn't check the disk, go to the disk tools and set it to do the check from there, or my preference is to boot from the windows installation disk, go to the recovery console and run 'chkdsk /p' from there. If things seem OK after that you can use gparted to expand the partition to full size again, then boot to Windows or use the XP installation disk to do another disk check.

If none of that works, I would suggest to copy all the data to somewhere else if you have not already done so, delete the partition, create a new partition, then copy the data back again.

Later, Seeker

---

### Post by coffeecat on 2009-11-02
> **zyxyellowxyz said:**
> ```
(X:)
1104.29 GB RAW
Healthy (Primary Partition)

```

I've come across this before. Sometimes - this only happens to some people - if you write to a NTFS partition with Linux using the ntfs-3g driver, Vista reports it as being "raw". Sometimes Vista can't read it, even though Linux/ntfs-3g can. Worst-case - if it's your Vista C: partition, Vista can become unbootable. This doesn't happern with XP. Don't know about W7.

When I last googled this issue there was a sense that this was more likely to happen with the 64-bit version of Vista. There were a few informative threads on [http://forum.ntfs-3g.org/](http://forum.ntfs-3g.org/) but that forum seems to have disappeared. If you try googling <vista raw ntfs> you might come up with something useful. But anyway, the suggestion from previous posters to copy all the data off with Ubuntu and then reformat seems sensible.

Out of interest, was this the C: partition, or another one?

---

### Post by zyxyellowxyz on 2009-11-13
Thanks for all the helpful replies. We, my husband and I, ended up backing up the most important of the data that was on that drive, and repartitioned it into 3 smaller partitions. Win7 has had no more problems since then. Sorry for the delay in my reply.

---

