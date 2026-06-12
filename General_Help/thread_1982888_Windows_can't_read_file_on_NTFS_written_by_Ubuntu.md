---
title: "Windows can't read file on NTFS written by Ubuntu"
date: 2012-05-19
forum: General Help
---

### Post by pinguinhood on 2012-05-19
Hi everyone!!!

I'm having some trouble with a dual boot configuration. I have Windows 7 and Ubuntu 12.04 with a shared NTFS data partition.
If I write files on this partition with Ubuntu I can see them until I boot Windows. In Windows I can't find those files and then if I boot up Ubuntu files seems to be disappeared.
The problem is that if I run chkdsk from Windows often files re-appear, but I have a 1Tb hard disk and it takes too much time doing it everytime!!!

Other info:
notebook: Samsung Series 7 Chronos NP700Z5A-S02IT
OS: Ubuntu 12.04 (64bit) + Windows 7 (64bit)

Partition:
/dev/sda1   ntfs   SYSTEM   (Windows)   boot
/dev/sda2   ntfs   Windows 7
/dev/sda3   extended                                  lda[INDENT]/dev/sda5   ntfs   Shared Partition
/dev/sda7   ext4   Ubuntu
/dev/sda6   linux-swap
[/INDENT]/dev/sda4   ntfs   RECOVERY                     diag

What could you suggest me?

Thanks in advance!

---

### Post by Mark Phelps on 2012-05-19
Don't know if THIS is your situation, but in many cases with laptops/notebooks, folks make the mistake of (1) hibernating Win7, (2) while Win7 is hibernated, writing/updating files on a shared NTFS partition from inside Ubuntu.

And then, when they go back into Win7, the file are gone!

This is because Win7 saves off the partition info (including the shared partition) when it hibernates.  When it is restarted, it then rewrites the partition info from what it saved -- effectively removing the changes that were made to the shared partition.

So, if you're hibernating Win7, the only choices you have are:
1) Stop writing to the shared drive from inside Ubuntu
2) Stop hibernating Win7.

---

