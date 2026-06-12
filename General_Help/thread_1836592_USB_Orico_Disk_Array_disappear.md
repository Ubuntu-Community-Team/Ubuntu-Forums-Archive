---
title: "USB Orico Disk Array disappear"
date: 2011-08-31
forum: General Help
---

### Post by seanxushen on 2011-08-31
This drive me almost crazy now. 

I have a Orico Disk Array, internally it runs RAID5 with 4* 2T hard disk and comes up with 6T total disk space. The 6T space is then formatted to to partition one 1T and another 5T, both are EXT3s.

The Disk Array connected to my Dell Latitude D630 Ubuntu via USB port.

The problem is the Disk Array will sometimes disappear (umount) itself. I thought it is power save problem, so I added a Cron job which copies a small file to the hard disk every  minutes. But that does not help, it will still periodically disappear. Also, I am running a bit torrent towards that disk array, so it should be always traffic written and read.

The only way I found that I can prevent the disk array goes down is to leave the desktop screen running. The desktop screen should not even go to screen saver mode nor switch off.

Very strange...any clue...

---

### Post by seanxushen on 2011-08-31
Anyone can help?

---

### Post by seanxushen on 2011-08-31
Need some one to help thanks

---

### Post by seanxushen on 2011-09-01
Still no one could give me any clue?

---

### Post by RikardSvenningsen on 2011-11-13
I have stumbled over this desperation.
You say you have a cron job running. I have discovered from other experiment that copy the same file to disc will not activate the disk enough.
You need to create the small file and delete it again, create a new file with another name and delete that file to.
If you do that you should keep the disk busy.

---

