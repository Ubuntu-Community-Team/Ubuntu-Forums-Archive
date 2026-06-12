---
title: "Ubuntu 9.10 stops working after update"
date: 2010-03-18
forum: General Help
---

### Post by pauliulian on 2010-03-18
I have Ubuntu 9.10 installed on my laptop.
The laptop has a single HDD with 2 partitions. Partition 1 has WindowsXP and partition 2 contains other data, among which the directory of the ubuntu installation. The partitions are formatted as NTFS.

Ubuntu has been installed with wubi on the second partition.

Ubuntu has been working fine for 2 days. Last night I updated the Ubuntu system and it required a restart. Needless to say, after the restart, grub wouldn't load. It just shows the shell.

I read the threads inside this forum and people usually manually select a kernel and boot up ubuntu, but when I do this, after I input all the commands I input "boot" and hit ENTER.

The computer starts booting up until a point when it says
ALERT! /host/ubuntu/disks/root.disk does not exist

and something about using selection #1 and exits to shell (Easy Shell or Easy Boot, I can't remember exactly what it says... Easy something anyway )

I've read that this is possibly caused by a NTFS dirty tag... but I do not see how to fix this problem.

Please, someone help me... I don't want to reinstall Ubuntu because I've been working on some things and they are saved inside Ubuntu.

---

### Post by pauliulian on 2010-03-19
I solved the problem by downloading the latest wubildr and copying it to C:\
After I did that everything worked fine.
The link to the new Wubildr can be found [here]("http://launchpadlibrarian.net/36920146/wubildr").

---

