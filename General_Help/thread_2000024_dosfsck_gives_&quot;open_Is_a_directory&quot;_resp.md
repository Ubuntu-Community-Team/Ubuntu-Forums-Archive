---
title: "dosfsck gives &quot;open: Is a directory&quot; response"
date: 2012-06-08
forum: General Help
---

### Post by anocide on 2012-06-08
Hello,

Background -

I have a Thunderbird shared profile on a FAT32 partition. It has decided it doesn't want to play anymore - I am fine with that. Want to move the profile and nuke it anyway. BUT, when backing up the profile, everything copies across except prefs.js which has all the mail account information (I have over a dozen so, yes, it is a big deal) - every time I try to copy it I get *"Error splicing file: Input/output error"*, so I suspect there is some damage on the partition. I then try and use dosfsck to see if it can be repaired, and it just gives -

[CENTER][B]*open: Is a directory*
[/B][/CENTER]

Using dosfsck 3.0.7 (24 Dec 2009) which Lucid tells me is current. Same response whether mounted or not. I cannot find anything on this message other than a Solaris FAQ which simply says the OS is confusing a file with a folder and nothing more.

Can anyone enlighten me? Or suggest a better way to try and fix FAT32 problems?

---

### Post by anocide on 2012-06-09
Resolved - took a lot of digging, found this error referencing SD cards -

[http://sdjf.esmartdesign.com/errors.html](http://sdjf.esmartdesign.com/errors.html)

> **Wrong Device Reference**

  Instead of /mnt/card/ or /mnt/cf, you must  use /dev/mmcda1 or /dev/hda1 to refer to your expansion card,  or you may get output like the following:[INDENT] bash-2.05# fsck.vfat /mnt/card/ 
dosfsck 2.8, 28 Feb 2001, FAT32, LFN
Read 512 bytes at 0:Is a directory
bash-2.05# [/INDENT]Referencing dev/sda6 (where my FAT is) instead of media/Fat32 worked.

---

