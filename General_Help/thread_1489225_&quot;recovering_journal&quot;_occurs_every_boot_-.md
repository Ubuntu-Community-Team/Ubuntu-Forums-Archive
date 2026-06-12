---
title: "&quot;recovering journal&quot; occurs every boot - Lucid / 10.04"
date: 2010-05-20
forum: General Help
---

### Post by pt85 on 2010-05-20
I'm wondering if someone can help.  I've recently upgraded two machines to 10.04 and both are displaying a strange behaviour on boot up.  Every boot, most if not all file systems are reporting "recovering journal" at boot up.  boot.log follows.
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
init: statd main process (1022) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1028) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1034) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1040) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1052) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1059) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1068) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1074) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1080) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1086) terminated with status 1
init: statd main process ended, respawning
init: statd main process (1092) terminated with status 1
init: statd respawning too fast, stopped
/dev/md3: clean, 16105/61952 files, 117831/246976 blocks
init: mounted-tmp main process (1132) terminated with status 127
mountall: Event failed
/dev/sdc1: clean, 179002/30531584 files, 89880682/122096000 blocks
init: ureadahead-other main process (1159) terminated with status 4
/dev/md2: recovering journal
usr: clean, 183066/625856 files, 1187703/2500080 blocks
var: recovering journal
/dev/md4: recovering journal
init: ureadahead-other main process (1194) terminated with status 4
/dev/md2: clean, 32144/883008 files, 900659/1765104 blocks
init: ureadahead-other main process (1208) terminated with status 4
/dev/md4: clean, 105/12181504 files, 14135635/48696992 blocks
var: clean, 17195/526240 files, 1209508/2098464 blocks
init: ureadahead-other main process (1229) terminated with status 4
init: ureadahead-other main process (1237) terminated with status 4
.....
```

Before this boot I booted a live CD and checked the status of the file system with dumpe2fs.  The two interesting lines were:
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem state:         clean

In particular why is the machine shutting down and the file system being left with the "needs_recovery" feature on?  This seems to be causing the journal recovery at boot.

By the way, the shutdown seems VERY fast - a lot faster than previous versions.  My suspicion is that the kernel is halting before the filesystems are dismounted or a bad dismount.

This might also be related to thread [1480187]("http://ubuntuforums.org/showthread.php?t=1480187").

Anyone with any suggestions?

Thanks

---

### Post by tekkenlord on 2010-09-11
Hello there. I have a similar (if not the same) behaviour on three Kubuntu 10.04 boxes. Have you found a solution to the problem? You may also want to take a look here:

[http://kubuntuforums.net/forums/index.php?topic=3113450.0](http://kubuntuforums.net/forums/index.php?topic=3113450.0)

---

### Post by Lukas666 on 2010-09-11
Slightly off topic, but how did you enable boot logging? In my Karmic 
/var/log/boot is always empty!

---

### Post by tekkenlord on 2010-09-12
/var/log/boot is empty for me too. However, the process during boot is stored in /var/log/dmesg. (or simply type in a terminal "dmesg")

---

