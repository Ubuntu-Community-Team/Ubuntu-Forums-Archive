---
title: "Command for listing partitions within LVM"
date: 2011-08-30
forum: General Help
---

### Post by tech291083 on 2011-08-30
Hi,

The fdisk -l command lists various partitions on the disk including a physical volume (LVM) if any as sda1, sda2 etc. But how do I know the partitions that reside within an LVM? The app Disk Utility is a GUI which is great, but what about the command line? Thanks

---

### Post by SidebySide on 2011-08-30
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by LiquidStranger on 2011-08-30
You could try pvs or pvdisplay. Both show a list of partitions that are part of a LVM Volume Group. pvs' output is very compact, but can show partitions that aren't part of any LVM Volume Group with the --all switch. pvdisplay shows more data, including allocation status and UUIDs.

---

