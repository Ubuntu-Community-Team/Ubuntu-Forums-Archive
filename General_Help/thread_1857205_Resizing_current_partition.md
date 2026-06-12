---
title: "Resizing current partition"
date: 2011-10-09
forum: General Help
---

### Post by canhoto on 2011-10-09
Hi.

In my HD I have Ubuntu and another distro (YDL) which I don't intend to keep using. So I would like to delete the partition where that one is and increase the size of the Ubuntu partition. How do I do that?

---

### Post by drs305 on 2011-10-09
This thread doesn't cover your situation exactly - I wrote it for expanding Ubuntu by taking space from Windows; the main points are the same however:
make a backup, use the LiveCD, unmount the partitions including swap, etc.

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

Make sure Ubuntu is controlling the boot process before you start deleting things and rebooting.

---

### Post by 3Miro on 2011-10-09
First BACKUP ALL IMPORTANT FILES. If you are inexperienced and you mess with partitions, you can easily lose all of your data. Now that you have been warned, if you don't backup and lose your files, then it will be entirely your fault.

Having said that, get a liveCD or liveUSB of Ubuntu (plenty of HowTo for those, you can use Google), then boot from the CD/USB and use Gparted. It is possible that deleting partitions can interfere with the boot-loader (especially if the deleted partition comes before the one that you increase in size), you may have to reinstall Grub (Ubuntu 10.04 and newer use Grub 2).

---

