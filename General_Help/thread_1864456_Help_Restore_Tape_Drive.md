---
title: "Help Restore Tape Drive"
date: 2011-10-19
forum: General Help
---

### Post by quartarian on 2011-10-19
Hello,

My mother in laws office HD died and her Secretary was using tape backups under Windows. I have no idea what software they were using and neither do they.

I've read up on mt and tar and I can successfully rewind the drive, but when I try to get the files I get an error message like:
# tar xvf /dev/st0
tar: Record size = 2 blocks
tar: This does not look like a tar archive
tar: Skipping to next header
tar: A lone zero block at 4
tar: Exiting with failure status due to previous errors

I couldn't get Windows 7 to recognize the scsi driver for the Tape. Is there any way to get the data of this tape drive from Linux? I've never used tape before and don't know what I'm doing.:(

---

### Post by quartarian on 2011-10-22
Wow, turns out this was actually pretty easy. I just installed Windows XP Pro on an extra HD I had and voilà. The tape drive was recognized and the built in backup/restore feature recognized the files.

---

