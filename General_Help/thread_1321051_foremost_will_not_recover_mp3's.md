---
title: "foremost will not recover mp3's"
date: 2009-11-09
forum: General Help
---

### Post by skadeet on 2009-11-09
I've been successfully using foremost to recover specific file types from a disk image.  However, the problem i'm facing now is that when i specify the mp3 extension foremost will not run, it'll just return the man page or something.
I've tried un-commenting the mp3 specific areas in the config file but no luck.

~$ foremost -t mp3 -i /path/to/image -o /path/to/output/directory/

other file types work just fine, not sure what's going on. has anyone else experienced this?  same thing is happening with tif's.

---

### Post by 0olong on 2009-11-10
mp3 isn't in the list of file types supported by Foremost, which I have to say is very disappointing. Have you tried using PhotoRec?

---

### Post by dimamali on 2009-12-10
Since foremost won't support .mp3 recovery is there any other way we can recover deleted .mp3 files from ntfs partitions...?

EDIT:
Indeed foremost does NOT support mp3 files. PhotoRec did the job for me.

---

