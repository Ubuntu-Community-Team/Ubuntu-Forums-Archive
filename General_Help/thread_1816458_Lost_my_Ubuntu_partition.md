---
title: "Lost my Ubuntu partition"
date: 2011-08-02
forum: General Help
---

### Post by mkowske on 2011-08-02
Hi all,

Today I lost my linux partition somehow. I booted up as normal and Ubuntu told me there was a problem on one of my partitons and I should run chkdsk /f in Windows (it is a NTFS part) and try rebooting then. So I did that, but mistakenly chose the Windows Recovery partition rather than my normal Vista partition and got a big fat ERROR screen because there was no c:\recovery.dat present. That seemed to have wiped my grub2 mbr. Fine no big deal, I booted my Unbuntu install/recovery disc so I could restore grub to the mbr but my 39 GB partition where Ubuntu SHOULD be is now listed as "Unallocated space". /dev/sda4 is nowhere to be found... but sda2 and sda5 remain.

So... before I do a reinstall, am I screwed? Is there anything else I can do? Maybe a better question... how the hell did this happen?

---

### Post by jerrrys on 2011-08-02
you can try testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by mkowske on 2011-08-02
Thank you. testdisk saved the day.

---

