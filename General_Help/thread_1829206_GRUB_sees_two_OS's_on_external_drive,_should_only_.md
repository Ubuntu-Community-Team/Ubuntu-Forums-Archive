---
title: "GRUB sees two OS's on external drive, should only be one"
date: 2011-08-20
forum: General Help
---

### Post by u-noob-tu on 2011-08-20
i recently started dual booting with Kubuntu using an external HDD. GRUB works fine, but it sees two Kubuntu's on the drive. In GRUB, i see "Ubuntu-Linux Kernel (for some reson its not identified as Kubuntu) on /dev/sdb1 (external drive)", then i see recovery mode beneath it, and the exact same line right below recovery mode, followed by another recovery mode. strangely, selecting either one boots into kubuntu no problem at all. is this a problem and is there anyway i can delete the duplicate entries?

---

### Post by oldfred on 2011-08-20
The last two digits should be different as every time it adds an update to the kernel it adds the new one to the top of the menu. You generally want to keep two versions in case one breaks you can boot with the older one.

We have seen one or two cases where two identical kernels were installed somehow. Then totoally duplicate entries will appear.

Post this:
grep menuentry /boot/grub/grub.cfg

How to remove older kernels:
Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

