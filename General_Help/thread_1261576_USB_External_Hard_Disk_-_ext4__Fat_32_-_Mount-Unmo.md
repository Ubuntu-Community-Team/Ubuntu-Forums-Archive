---
title: "USB External Hard Disk - ext4 / Fat 32 - Mount-Unmount"
date: 2009-09-08
forum: General Help
---

### Post by nomnex on 2009-09-08
Alright, I have got my USB HD formated as follow 200 GB ext4 - 150 GB ext4 - 50 GB Fat32 and thanks to the forum help (nothingspecial), I could set the correct permissions.

Now here is the next question:

One HD with 3 partitions - when I plug-in 3 icons show up on the Desktop and in the places menu under computer (nothing special there)

When I need to remove the disk - I have to right-click and select for each partition Unmount (3 clicks). Is there a way to unmount ALL the partitions for a usb disk in ONE click?

a. using the GUI - Nautilus here (Jaunty)
b. using the CLI - bash

Thanks

---

### Post by fragos on 2009-09-09
I would wonder if creating a Logical Volume LVM might lead you to a solution. The following link may be helpful.

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by fragos on 2009-09-09
I would wonder if creating a Logical Volume LVM might lead you to a solution. The following link may be helpful.

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by nomnex on 2009-09-09
Hi there, no that does not.
I just need a quick way to umount all the partitions of a USB HD vs. umounting them one by one.
a) using Nautilus
b) using Bash

---

