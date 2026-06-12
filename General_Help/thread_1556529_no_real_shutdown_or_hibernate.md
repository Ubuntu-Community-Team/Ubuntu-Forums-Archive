---
title: "no real shutdown or hibernate"
date: 2010-08-19
forum: General Help
---

### Post by sunfish on 2010-08-19
I've installed Lubuntu on my old Armada 1700 laptop. It's used as an audio server. The only thing I can't figure out is why it doesn't power down my machine (like all the other distros I've used). It bails out of both shutdown and hibernate with a screen message that either the system has been halted or instructions to manually power down my machine.

As I said, any other OS I've used on this machine will actually kill the power after a clean halt or hibernate procedure. What's up with Lubuntu?

After I DO hit the power button the laptop waits about 4 seconds and then powers on and reboots!!! WTF?

---

### Post by phillw on 2010-08-20
Hi,

the first thing to check is your RAM Vs SWAP area. As I'm sure you know, you need SWAP >= RAM for hibernation / suspend to work. Issuing ```
sudo fdisk -l
``` will result in entries similar to >    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   b  W95 FAT32
/dev/sda2           12749       43345   245770372    5  Extended
/dev/sda3           43346       43600     2048287+  82  Linux swap / Solaris
The line of interest is number of blocks for Linux swap (2048287) on my system. Next ```
free
``` will return something similar to >              total       used       free     shared    buffers     cached
Mem:       1534516     873552     660964          0      88880     353204
 In this case, the number of interest is the 1534516. This number must be less or equal to the swap area. If you do have enough swap, then [Swap FAQ's](https://help.ubuntu.com/community/SwapFaq) has how to increase it (if like me, you have more swap area than physical memory, it will do no harm).

Regards,

Phill.

---

### Post by sunfish on 2010-08-21
Perhaps I wasn't clear. The machine DOES hibernate. That is not the problem. The problem is that after it goes into hibernation the laptop does not shut down. The power stays on and the wireless card is still lit.

I think I may have solved the problem though. I added "acpi=force" as a kernel option in my grub.conf file and now it does power off after hibernation and/or shutdown.

---

