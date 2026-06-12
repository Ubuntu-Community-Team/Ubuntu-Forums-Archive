---
title: "Restoring /boot partition"
date: 2010-06-07
forum: General Help
---

### Post by defmer on 2010-06-07
I accidentally formated the /boot partition with gparted and i realized the mistake and have not restarted the system yet. when I look at the gparted its showing me the partition has boot flag set and is in ext3 file system. 
here are a couple of questions.

1) when I do a cd /boot. I am able to see the following files and so I am not sure what was formated. 

abi-2.6.27-17-generic
config-2.6.27-17-generic
config-2.6.27-7-generic
grub
initrd.img-2.6.27-17-generic
initrd.img-2.6.27-7-generic
memtest86+.bin
System.map-2.6.27-17-generic
System.map-2.6.27-7-generic
vmcoreinfo-2.6.27-17-generic
vmcoreinfo-2.6.27-7-generic
vmlinuz-2.6.27-17-generic
vmlinuz-2.6.27-7-generic


Am I supposed to see these files if I formated /boot using gparted?

2) How do I make sure that the boot partition is still intact?
3) how to I make sure that all partitions are still intact?

thank you

---

### Post by Ozymandias_117 on 2010-06-07
Are you sure you're looking at that partition? The partition would have to have been unmounted to reformat it. Use ```
mount
``` to see if it is still really mounted.

---

### Post by defmer on 2010-06-07
I did not see /boot in the list after the entered the command "mount" and also "mount | grep boot" returned nothing.

but I just copied all the files (listed above), from /boot to a folder in my home directory. so the files are still present in /boot partition


so what should I do/try next?

---

### Post by oldfred on 2010-06-07
Boot flag is not used by linux/grub, so that would have nothing to do with booting in linux. To see how you are booting run this from the liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

If you did format the partition testdisk may be able to recover it.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by Ozymandias_117 on 2010-06-07
It sounds to me like you're looking at a /boot that Ubuntu put in /boot on it's partition before you mounted your /boot partition and set it up that way. Can you mount the partition you use for /boot and make sure there are things in it?

---

