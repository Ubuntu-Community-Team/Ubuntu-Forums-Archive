---
title: "Can't mount a DVD which works fine in windows."
date: 2011-06-27
forum: General Help
---

### Post by New00Folder on 2011-06-27
So a friend mailed me a DVD today. It's not a video or a movie DVD; just some files and folders burned on it and I can read them all without a glitch on my machine when I'm running windows7.

Different story in ubuntu though. The disc rotates then it's all calm after a while. Browser doesn't automatically display the contents of the disc which it does when I insert other DVDs. That should rule out hardware issues. The DVD drive icon from My Computer is gone too. Inserting the DVD adds nothing to the dmesg output. To sum up, the system acts as if it has lost the use of it's DVD drive.

Things that might be at the root of this are:
1> The disc might not be finalized.
2> Multisession disc.

Please help me find out what's wrong with the disc and how to deal with it making the least possible use of windows.

---

### Post by Beacon11 on 2011-06-27
Have you tried mounting the DVD from the terminal?

---

### Post by New00Folder on 2011-06-27
This is definitely a multisession unfinalized DVD burned by explorer.exe in windows7.

> sudo mount /dev/sr0 /media/cdrom0

produces:

> mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Nothing is added to syslog.

But if I try
> sudo mount /dev/sr0 /media/cdrom0 -t udf
(This is a udfs as reported in windows.)
additions to syslog are:
> [  867.063351] UDF-fs: No VRS found
[  867.063357] UDF-fs: No partition found (1)

---

### Post by Beacon11 on 2011-06-28
Two things: What is the result of:

```
file -s /dev/sr0
```

and have you tried mounting with iso9660?

---

### Post by New00Folder on 2011-06-28
Output of > file -s /dev/sr0 is > /dev/sr0: data

Command > sudo mount /dev/sr0 /media/cdrom0 -t iso9660 gives > mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 			 		

Addition to syslog is > ISOFS: Unable to identify CD-ROM format.

---

