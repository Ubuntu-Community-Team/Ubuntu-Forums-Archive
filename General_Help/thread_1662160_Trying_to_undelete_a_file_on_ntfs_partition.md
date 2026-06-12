---
title: "Trying to undelete a file on ntfs partition"
date: 2011-01-07
forum: General Help
---

### Post by axeman71 on 2011-01-07
I dual boot with Win7 and Ubuntu.  I have several different partitions including one named "Music" which is NTFS and does not have either OS installed on it so it only gets written to when I am doing my music recording.

I recently created a file named "all music backup" on the partition Music using a program in Ubuntu.  The backup contained a number of songs I had recorded and wanted to backup all in one place.  It was a very large file (7-8 GB I think, I don't remember exactly).  I then deleted the individual files I had backed up.  A few days later I was in Ubuntu and noticed that my backup file had disappeared and some (but not all) of the individual files I had deleted and re-appeared.  I rebooted to Win7 and used 2 different undelete utilities to try and find the missing file but neither program could find it.  I booted back to Ubuntu and tried TestDisk but it didn't find the missing file either.  I don't know what happened to it but I am sure I did not delete it.  I don't fully understand NTFS partitions but I fear there was some kind of problem between Win7 and Ubuntu and one of the OS's messed up the partition table.  

I have not used the Music partition recently and I am sure the file has not been written over with new data.  It should still be there but I don't know how to find it.  Any ideas?

---

### Post by Quackers on 2011-01-07
You could give testdisk a try (install via synaptic)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by axeman71 on 2011-01-07
I did try TestDisk after trying the 2 windows programs.  It finds plenty of deleted files but the backup file that is missing (and the original files I deleted after making the backup) are not on the list for potential recovery.

---

### Post by Quackers on 2011-01-07
I haven't used either myself (fortunately) but I believe photorec can do good things. I'm not sure if it's part of testdisk or not though.

---

