---
title: "Removing items from the boot (grub2) menu"
date: 2011-01-09
forum: General Help
---

### Post by hornetster on 2011-01-09
Have recently installed 10.10 and have several other OS' installed, as well as other NTFS (non-OS) partitions. After a couple of updates, my boot menu shows about 8 entries, whereas I should only have about 4...
How is this fixed in Grub2?
Thanks, John

Have installed Startup Manager, and there seems to be no option here...

---

### Post by PokerJoker on 2011-01-09
Looking for the same info :)

Startupmanager is grub not grub2 i believe. Here's an interesting link to a wiki with most info: 
[http://en.gentoo-wiki.com/wiki/Grub2]("http://en.gentoo-wiki.com/wiki/Grub2")

The files in /etc/grub.d/ seem to be the entries in the boot (grub2) menu, changing the prefix (20_ ..) changes the order in the menu...still reading to find out how to remove entries.....
thought to post it anyway

---

### Post by TeoBigusGeekus on 2011-01-09
See [here]("http://ubuntuforums.org/showthread.php?t=1662483").

---

### Post by ajgreeny on 2011-01-09
If you have several OSs on the machine it is no surprise that you have up to 8 entries on the menu.

Let's see what your menu shows you by posting the output in terminal of ```
grep menuentry /boot/grub/grub.cfg
``` You may be asking an un-necessary question in the first place.

---

