---
title: "ddrescue corrupted drive with data on"
date: 2010-10-13
forum: General Help
---

### Post by IceblueGen3 on 2010-10-13
I was trying to read data off a damaged hard drive and used ddrescue and followed the instructions on this site:
[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

It kept giving me an error when I typed in
```
sudo dd_rescue /dev/sda1 /dev/sda2/backup.img
```so I eventually removed the backup.img part and it started working.

I then checked the drive it was writing to and discovered that no folder or file had been created and I assumed that it was overwriting the entire drive so I cancelled it immediately (about 20-30 seconds after I started it).

Now the drive that it started writing to shows as 'unknown' in the disk utility program. It couldn't have overwritten much in the time because it was struggling to read the source disk.

How do I get the disk recognisable again? And possibly recover the data which may have been overwritten before I stopped it.

---

