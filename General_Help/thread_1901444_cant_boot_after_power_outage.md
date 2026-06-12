---
title: "cant boot after power outage"
date: 2011-12-28
forum: General Help
---

### Post by rrobertt on 2011-12-28
I have a dual boot setup with windows xp and ubuntu 11.10. This morning I had a power outage and ubuntu will not boot up now. Windows boots up ok and the grub menu seems to be working. When I attempt to boot into ubuntu I get this "(initramfs) ata_id[272]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument". I let it sit like that for a few minutes and nothing happens. I am new to ubuntu so I would appreciate detailed help, thanks.

---

### Post by sohmc on 2011-12-28
Without more information, my guess is that your disk got damaged during the power outage.  Try booting from a live CD to see if you can read the linux partition.  If you can read the partition, you may get away with a simple "repair" of the OS.  If not, then your hard drive has become damaged and should replace it.

---

### Post by rrobertt on 2011-12-29
I dont know what information to provide but I will add this part of the error message that I omitted in my first post. "BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash) Enter 'help' for a list of built-in commands". I also used gparted through a live cd to delete the ubuntu partition and swap file. I then reinstalled ubuntu 11.10, everything went fine but I got the same error message on boot up. I also used Disk Utility and it says my disk is healthy, ran check filesystem on ubuntu partition and got filesystem is clean. Also windows xp is on the same hard drive and it boots up fine on grub 1.99. I will keep searching the web for info and would appreciate any help from this forum, thanks again.

---

