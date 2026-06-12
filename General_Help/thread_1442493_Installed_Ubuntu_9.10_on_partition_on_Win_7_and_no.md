---
title: "Installed Ubuntu 9.10 on partition on Win 7 and no GRUB?"
date: 2010-03-30
forum: General Help
---

### Post by rmjohnson144 on 2010-03-30
I just finished installing Ubuntu 9.10 on my Windows 7 1TB hard drive and after installation I just get Windows 7 multi-boot screen with no Ubuntu and no GRUB.

I have two other hard drives at the moment with Windows on them for troubleshooting or just in case my drive fails.

anyway, where did GRUB go?  It installed successfully and I was in Ubuntu until I rebooted.

What gives
-=Mark=-

---

### Post by Mark Phelps on 2010-03-30
Was this a Wubi install? Or did you create separate partitions and install Ubuntu to those?

IF the second, and you can boot into Ubuntu, open a terminal and enter "sudo update-grub".  That should generate a new GRUB 2 menu with an entry for Win7.

---

### Post by rmjohnson144 on 2010-03-30
The problem seems to be the installation goes by controller number, rather than selected boot device.  So grub installed on sata controller 1 and my boot was controller 3. hence, it installed on sda while installing from sdc.  it has a weird numbering scheme.  sata ports 1 and 3 are sda and sdb and sata 2 and 4 are sdc and sdd

But thanks for the update-grub command for fixing things in the future.  I get grub errors all the time when I change things on my system.  especially with 4 HDDs.

oh, and no this wasn't a wubi install.  It has big problems last time I tried it, so maybe next version of ubuntu I may give it another go.

Thanks
-=Mark=-

---

