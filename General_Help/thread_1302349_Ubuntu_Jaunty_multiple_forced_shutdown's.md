---
title: "Ubuntu Jaunty: multiple forced shutdown's"
date: 2009-10-27
forum: General Help
---

### Post by TuLesto on 2009-10-27
VLC has been acting up lately it seems like whenever I double click on the video to evoke a full-screen or drag the bar (that determines the time I want at in the video) my computer crashes i am then forced to do a hard shutdown and am prompted a while later to do a manual check with fsck. 

My question pretty much amounts to this: Should I go ahead with it and do the check? 
----------------
Log of fsck -C3 -R -A -a 
Mon Oct 26 17:22:54 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda5 was not cleanly unmounted, check forced.
/dev/sda5: 44/498736 files (13.6% non-contiguous), 103972/995998 blocks
/dev/sda7 contains a file system with errors, check forced.
/dev/sda7: Unattached inode 5472260


/dev/sda7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
fsck died with exit status 5

Mon Oct 26 17:25:00 2009
----------------

Log of fsck -C3 -a -t ext2 /dev/sda3 
Mon Oct 26 17:22:53 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda3: clean, 158763/3751936 files, 1039305/7500346 blocks

Mon Oct 26 17:22:53 2009
----------------

---

### Post by ScarySquirrel on 2010-04-24
Of course you should. I mean, why not?

This should clear things up: 
[IMG]http://icanhascheezburger.files.wordpress.com/2007/08/error-reboot-plz.jpg[/IMG]

---

