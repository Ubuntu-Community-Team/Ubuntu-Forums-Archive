---
title: "Can't boot after using dd injudiciously"
date: 2012-04-15
forum: General Help
---

### Post by mhemmelm on 2012-04-15
So I used the dd command to mount an iso of the knoppix os to what I though was my flash drive but turned out to be my hard drive. Now when I boot I go immediately into grub rescue, and if I try to use ls on any of my partitions I get an 'unknown filesystem' error. I tried using boot repair from a live boot of ubuntu, and was told that there was no os on the computer. This is the Boot Info report: [http://paste.ubuntu.com/931958/](http://paste.ubuntu.com/931958/)
Any help would be much appreciated.

---

### Post by dcstar on 2012-04-16
> **mhemmelm said:**
> So **I used the dd command to mount an iso** of the knoppix os to what I though was my flash drive but turned out to be my hard drive.


The "dd" command does **not** "mount" anything in any shape or form, it is a command for copying data from one block device to another so if you have used it then **you have wiped whatever the destination was**.

Reinstall, all of your data is gone.

---

