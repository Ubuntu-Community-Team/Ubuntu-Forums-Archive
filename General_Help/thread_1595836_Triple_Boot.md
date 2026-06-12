---
title: "Triple Boot"
date: 2010-10-13
forum: General Help
---

### Post by beakieman on 2010-10-13
OK, so I installed Ubuntu for the first time last week...

I already had Windows XP and Windows 7 installed.

When I boot up I first of all get the Ubuntu bootloader. If I choose "Windows 7", I get taken to the Windows 7 bootloader where I can choose which Windows I want to run.

Anyone know what I need to do to get GRUB to let me boot up from either of the 3 OS (therefore, only having to deal with 1 bootloader each time I start.

I don't know anything about Ubuntu so please explain yourself fully :)

Thanks

---

### Post by oldfred on 2010-10-13
welcome to the forums:

It is part of windows. I do have links on how to make it work if you are installing but not sure about repair to make it work after install. The second install of windows has its boot files moved to the partition with the first install (active partition).

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Are both windows in primary partitions? If so you could try moving boot flag (active partition in windows) and repair the second install.

---

