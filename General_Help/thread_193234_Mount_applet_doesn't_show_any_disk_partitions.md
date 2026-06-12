---
title: "Mount applet doesn't show any disk partitions"
date: 2006-06-09
forum: General Help
---

### Post by cas_ on 2006-06-09
Hello!

After upgrading Breezy to Dapper, I have a problem with gnome mount applet, which stopped showing any hard drives partitions. It shows both of my CD/DVD drives, and my floppy drive (with wrong icon however;it uses an icon that should represent a hard drive rather than a floppy). I must add that before upgrading, everything worked just fine. The old version used to show all mount points defined in /etc/fstab. I haven't changed anything in my fstab.

---

### Post by cas_ on 2006-06-10
I consider this as a bug. I've just made a fresh dapper install on another partition. At first my partitions were present both in mount applet and on the desktop. However after changing their fstab options, so that they are not mounted automatically (by adding "noauto,users"), they have dissapeared. Drive mounting applet shows only my computer's floppy. It definitely should work differently, because now the applet is almost useless and I have to mount drives from the cli.

---

