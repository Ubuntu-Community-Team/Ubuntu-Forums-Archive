---
title: "RSYNC skips some files"
date: 2010-07-21
forum: General Help
---

### Post by stevo1977 on 2010-07-21
I run 'rsync -ua --delete' to keep an EXT3 partition on a flash drive synced with a folder on my home partition.  RSYNC gives no errors, but at times it fails to update certain files while correctly updating others.  Some of them are TEX files and some are ODS files, and in each case I double-checked to see that the mod-time on the source file is newer than on the destination.  I tried adding 'i' and 'v' to the command to debug, but this is all the output RSYNC gives me:

sending incremental file list

sent 18706 bytes  received 53 bytes  37518.00 bytes/sec
total size is 45874824  speedup is 2445.48

Any ideas on what's happening or how I can debug this issue?  Thanks.

Cheers,
stevo

---

### Post by stevo1977 on 2010-07-21
I realized later this morning that more information might be helpful.

I actually use an EXT3 flash drive as an intermediary to sync my work computer (eeebuntu 8.10) with my home computer (ubuntu 9.10).  Sometimes (not always), files do not sync from the flash drive to the computer, but syncing almost always works computer >> flash drive.  I had thought this was because the flash drive was FAT32, but reformatting to EXT3 has not resolved the issue.

Again, any insights or help would be most appreciated.

Cheers,
stevo

---

### Post by AlphaLexman on 2010-07-21
Have you tried the '-v' verbose option?
Also from the rsync man page, these looked like they might be of your interest:
```
--itemize-changes       output a change-summary for all updates
--out-format=FORMAT     output updates using the specified FORMAT
--log-file=FILE         log what we're doing to the specified FILE
--log-file-format=FMT   log updates using the specified FMT

```

---

### Post by stevo1977 on 2010-07-22
Thanks, AlphaLexman.  I actually used those parameters (that's what '-i' is supposed to do) and sent the output to a log file; that's how I got the segment that I quoted in the first post.  I appreciate the help, though.

Cheers,
stevo

---

### Post by iponeverything on 2010-07-22
It seems to me like the copy in the memory buffer cache is different than the one on the platter.. This shouldn't be the case. Test the theory by rebooting the machine to see if it sync's right.

---

