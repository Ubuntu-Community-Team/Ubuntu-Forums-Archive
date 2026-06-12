---
title: "Tips for recovering partition with testdisk"
date: 2011-09-30
forum: General Help
---

### Post by sammya on 2011-09-30
So I plan to recover files that were deleted that were inside the partition i mistakenly deleted. I have an external hdd to back the files onto.. but was just curious about the steps I will have to take to make this possible.

I am currently booting from Ubuntu Live-USB (11.04). Any help is much appreciated.

Thanks

Sam

---

### Post by dcstar on 2011-09-30
> **sammya said:**
> So I plan to recover files that were deleted that were inside the partition i mistakenly deleted. I have an external hdd to back the files onto.. but was just curious about the steps I will have to take to make this possible.

I am currently booting from Ubuntu Live-USB (11.04). Any help is much appreciated.


Read one of the many existing HOWTOs and follow their instructions.

---

### Post by oldfred on 2011-09-30
I recovered data with photorec. If partition mounts testdisk may show files and that is better as they will still have names. Photorec just scans drive looking for file signatures and writes that data to your other drive. It may recover more than you have as bits of files will also be recovered. I had text files that I had updated a lot and it recovered the same file many times. Lots of grepping and comparing to get close to final version but I am not sure I ever recovered last saved.

Process with photorec takes a long time and only has file extensions. But some files have internal name that you can use to rename.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

