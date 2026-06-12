---
title: "Strange rsync/external harddrive problem"
date: 2011-01-05
forum: General Help
---

### Post by ronzo on 2011-01-05
I've been backing up a server using rsync for a couple of years now without encountering any problems... but...

Recently I've changed one of the two external usb hard drives to a WD Elements 2TB drive. That's were the problems started...

I can start the backup manually and it seems to run properly... but after a while I cannot ping or SSH the server anymore - the server hangs. Due to the fact that I have no monitor connected, I cannot definitely say what has happened. (sometimes I can ping, but not SSH; sometimes I can establish an SSH connection but after I try to login I get the message 'server closed the connection') I could not find anything in the log files after a hard-reset (or maybe I did not look into the right one?)...

I do not think it has anything to to with the system load because I can use the server quite normally when backing up to the first external drive (1,5 TB WD Elements).

What would you suggest to track down the problem?

Here's what I will try next:
1) try suspicious external drive on another computer
2) if it still shows a similar behaviour, replace the USB cable
3) try attaching a monitor to the server to see if it reveals further information
4) if none of these measures help, what next?

Thanks a lot in advance for your input!

-- 
Here are some details concerning my server setup:
Internal storage: RAID5
Two external backup drives (one 1,5 TB WD Elements New, one 2TB WD Elements New (the problematic drive))
OS: 64bit Ubuntu Maverick Server with all updates
FS: XFS on the source FS, XFS on the external drives (2TB drive partitioned and formatted in order to comply with 4k sectors)

---

