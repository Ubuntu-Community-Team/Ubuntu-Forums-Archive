---
title: "Wubi refused to work even after chkdsk /r"
date: 2010-05-08
forum: General Help
---

### Post by paulehoffman on 2010-05-08
Try (hd0,0): NTFS5: 2
Try (hd0,1): invalid or null
Try (hd0,2): NTFS5: No wubildr
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.

Following the advice in the FAQ, I went into Windows, opened an admin
shell, did 'chkdsk /r', had it schedule this for the next boot, and
rebooted. chkdsk found a buttload of errors and said it fixed them.
Just for safety's sake, I deleted the entire folder in which the
problems occurred and emptied the recycle bin.

I then tried to boot into Ubuntu again, but got the same problem as
above. So I went into Windows, did 'chkdsk /r', rebooted, and saw that
Windows found no errors. I tried Ubuntu again, but had the same
results as above. Because I didn't have much in the Ubuntu build,
I uninstalled it, which apparently went fine. I then did a clean
Wubi install, which also apparently went fine. However, on the
reboot, you guessed it: the same problem as above. I even tried
both -i386 and -amd64: same failure.

chkdsk is telling me that there are no problems:

C:\Windows\system32>chkdsk
The type of the file system is NTFS.
Volume label is HP.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
  622848 file records processed.
File verification completed.
  273 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  60 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
  663044 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  622848 file SDs/SIDs processed.
Security descriptor verification completed.
  20099 data files processed.
CHKDSK is verifying Usn Journal...
  37567544 USN bytes processed.
Usn Journal verification completed.
Windows has checked the file system and found no problems.

 341847099 KB total disk space.
 157363208 KB in 95849 files.
     55008 KB in 20100 indexes.
         0 KB in bad sectors.
    736523 KB in use by the system.
     65536 KB occupied by the log file.
 183692360 KB available on disk.

      4096 bytes in each allocation unit.
  85461774 total allocation units on disk.
  45923090 allocation units available on disk.

The Ubuntu directory has stuff in it:

C:\ubuntu\winboot>ls -la
total 100
drwx------+ 1 Administrators None     0 2010-05-08 15:45 .
drwx------+ 1 Administrators None     0 2010-05-08 15:45 ..
-rwx------+ 1 Administrators None 88813 2010-05-08 15:44 wubildr
-rwx------+ 1 Administrators None  1270 2010-05-08 15:44 wubildr.cfg
-rwx------+ 1 Administrators None  8192 2010-05-08 15:44 wubildr.mbr

C:\ubuntu\disks>ls -la
total 17408000
drwx------+ 1 Administrators None           0 2010-05-07 17:26 .
drwx------+ 1 Administrators None           0 2010-05-07 17:23 ..
drwx------+ 1 Administrators None           0 2010-05-07 17:23 boot
-rwx------+ 1 Administrators None 17557356544 2010-05-07 17:26 root.disk
-rwx------+ 1 Administrators None   268435456 2010-05-07 17:26 swap.disk

But the boot/grub does not (I don't know if it is supposed to):

C:\ubuntu\disks>ls -la boot
total 0
drwx------+ 1 Administrators None 0 2010-05-07 17:23 .
drwx------+ 1 Administrators None 0 2010-05-07 17:26 ..
drwx------+ 1 Administrators None 0 2010-05-07 17:23 grub

C:\ubuntu\disks>cd boot

C:\ubuntu\disks\boot>ls -la grub
total 0
drwx------+ 1 Administrators None 0 2010-05-07 17:23 .
drwx------+ 1 Administrators None 0 2010-05-07 17:23 ..

Any clues would be appreciated.

---

### Post by paulehoffman on 2010-05-16
Bump. It's been a week, but no one has any clues?

---

