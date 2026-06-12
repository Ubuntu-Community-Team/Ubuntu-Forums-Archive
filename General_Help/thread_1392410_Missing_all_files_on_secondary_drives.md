---
title: "Missing all files on secondary drives"
date: 2010-01-28
forum: General Help
---

### Post by Amorget on 2010-01-28
My system is setup like this: 1 250 gb HDD, with a 20 gig partition for /, 200 gigs for /home and the rest is a swap file.  I also have a 1 TB (ext3) and 1.5TB (ext4) hard drive that are also installed, mounted to /Shared_1TB and /Shared_15TB

I just installed Ubuntu 9.10 and everything seemed to be fine.  I installed all the updates, install the Nvidia proprietary drivers and got my HDMI audio working.  I went to try and play a video to see what would happen.... there are no files in /Shared_1TB.  It is totally blank.  I tried making myself the owner, and while this worked it didn't help anything.  I tried unmounting and remounted, however it kept saying it was busy and wouldn't remount it.  At this point I was a little panicked, so I threw in a LiveCD and low and behold once I mount it in the LiveCD all my files are there.  Phew.

So, does anyone have any ideas why all my files are missing on the 1TB drive?

Thanks,
Douglas

---

### Post by alwayshere on 2010-01-28
there is a bug with big files with ext4  maybe worth looking into ?

---

### Post by Amorget on 2010-01-28
The FS on that drive is Ext3  :(

---

### Post by MaindotC on 2010-01-28
Just add an entry in /etc/fstab to get it mounted permanently.  Also if you're in the directory you're trying to unmount/mount then you'll typically get that error message.

---

### Post by Amorget on 2010-01-28
It is mounted permanentaly.  In my original installation during the parition editor I manually added it so it is added to the fstab.  My umount/mount was just to see if something was messed up with the mount somehow.  I had no problems mounting my 1.5 TB drive to that same location, and it was already even mounted to another location.

---

### Post by Morbius1 on 2010-01-28
Basic information please. Post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

---

