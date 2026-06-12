---
title: "External HDD error"
date: 2011-10-08
forum: General Help
---

### Post by meem1029 on 2011-10-08
So I went out and bought a fancy new Western Digital HDD for external backup.  I brought it home and formatted it so I could use it in Ubuntu.  I used NTFS since I dual boot with windows and want it accessible from there if need be.  I then used fwbackups to back it up.  It gave me some odd error after working for like a day.  This seemed odd already since it didn't seem like it should take that long (320 gb internal hdd in my laptop). I just ignored the error and went on with my life.  Now I just plugged it in again (I know, terrible habits for backup) and Ubuntu wouldn't mount it.  The error it gave is:


Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Any ideas on what can be done to fix this?  Would it be best to just reformat that partition and do the backup again?

Thanks for the help!

---

### Post by dcstar on 2011-10-08
> **meem1029 said:**
> So I went out and bought a fancy new Western Digital HDD for external backup.  I brought it home and formatted it so I could use it in Ubuntu.  I used NTFS since I dual boot with windows and want it accessible from there if need be.  I then used fwbackups to back it up.  It gave me some odd error after working for like a day.  This seemed odd already since it didn't seem like it should take that long (320 gb internal hdd in my laptop). I just ignored the error and went on with my life.  Now I just plugged it in again (I know, terrible habits for backup) and Ubuntu wouldn't mount it.  The error it gave is:


Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Any ideas on what can be done to fix this?  Would it be best to just reformat that partition and do the backup again?

Thanks for the help!

Install **gparted** and use that to do a Check on the partition - or manually use **fsck** in a terminal to do the same thing. You can also reformat it if you don't need any data on it.

Be aware that drives are more prone to failing when very young or very old, so it is also possible that the hardware is faulty.

---

### Post by fchaffin on 2011-10-08
It sounds like the NTFS MFT got messed up.  I have 4 external USB drives that I share between Ubuntu and Windows.  I found the best solution is to format the drive as FAT32.  I format under Ubuntu and use GParted to create/re-size partition if needed.

---

### Post by jazzon on 2011-10-08
only drawback to fat32 is 4gb file size limit, so if you take that route be aware of this limit.  It is built into fat 32.

---

### Post by meem1029 on 2011-10-09
After waiting for a bit (I'm not the most patient), I just went ahead and reformatted since the only data was a backup I had made.  It seems to be working now.

Thanks for the replies.

---

