---
title: "Vista can't recognise NTFS partition"
date: 2009-07-25
forum: General Help
---

### Post by anandamide on 2009-07-25
Hey everybody :-)
I have a separate NTFS partition on sda6 containing all my media files. Vista, for some reason, has stopped reading this partition. It can see 'E', but can't see available space or open the drive. Every time I go into Windows chkdsk  is automatically run on the partition (which always comes back as being OK). 

This happened a while back so I can't remember exactly what steps led up to it (never simple, eh?), but it's increasingly annoying as my music is locked out while I'm in Vista. 

Any ideas? Linux is perfectly happy. I've checked under gparted for any weird flags but the partition is clear. Calls for me to migrate fully to Linux will be ignored unless accompanied by an offer to buy me a license for SPSS 17, currently retailing for the bargain price of £1,169 ;-)

---

### Post by merlinus on 2009-07-25
Did you install linux using wubi, or in separate partitions?

You can install ntfsprogs in linux, and use that for troubleshooting your music partition.

Also, did you try running chkdsk with the /f parameter?

---

### Post by bodhi.zazen on 2009-07-25
If it is working from Ubuntu then it sounds like a windows problem.

We are trying to direct Fedora questions to the Fedora forums and Debian to Debian.

In your case I suggest you try a windows forum.

---

### Post by synapsys on 2009-07-25
For best results, make a complete backup of sda6 in ubuntu. Then, reformat the partition as ntfs **from vista**. Then boot back into ubuntu and restore your backup to the partition. That way both os' will be happy.

---

