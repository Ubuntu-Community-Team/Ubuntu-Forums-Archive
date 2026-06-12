---
title: "upgrading kernel, raid1"
date: 2009-11-02
forum: General Help
---

### Post by ubdime on 2009-11-02
I currently use a raid1 for Ubuntu that I installed via the alternate cd. Since then, everything worked well. Upgrades come and go. I think I went through 2 (8.04 to 8.10 to 9.04) distribution upgrades with it.

Recently, I was building a new computer that I also wanted to run raid1 on, except this computer didn't have a second ide controller (both hard drives are ide and I don't have a sata cdrom).

So I...
1. installed 9.04 to 1 hard drive
2. unplugged cdrom and plugged in second hard drive
3. created identical partitions of type linux raid on second hard drive
4. created a raid1 with 2 disks with 1 missing and the 2nd hard drive
5. mounted and rsync'd first hard drive onto degraded raid1
6. setup grub on 2nd hard drive
7. booted off 2nd hard drive, then repartitioned first hd to linux raid
8. added 1st hard drive to raid1 and let it rebuild
9. setup grub again on both
10. added the raid uuid to mdadm.conf
11. ran update-initramfs to update mdadm.conf

So this seemed to work great. Except then I upgraded to 9.10. And when it used the new menu.lst from grub, it now loads into grub with "Error 15: File not found" and when I go to edit grub, I no longer have the piece of paper that I wrote down all the uuid's on.

All 5 options, Ubuntu 9.10 kernel 2.6.31-14-generic, (recovery mode), 2.6.28-16-generic, (recovery mode), and even memtest all give the same error.

This is a brand new system so I haven't lost anything. I could just as easily install 9.10 from a new cd and follow the same steps. But I don't want to run into this problem in the future during kernel upgrades. Does anyone know what I missed?

---

### Post by dcstar on 2009-11-02
> **ubdime said:**
> 
......
So this seemed to work great. Except then I upgraded to 9.10. And when it used the new menu.lst from grub, it now loads into grub with "Error 15: File not found" and when I go to edit grub, I no longer have the piece of paper that I wrote down all the uuid's on.

All 5 options, Ubuntu 9.10 kernel 2.6.31-14-generic, (recovery mode), 2.6.28-16-generic, (recovery mode), and even memtest all give the same error.

This is a brand new system so I haven't lost anything. I could just as easily install 9.10 from a new cd and follow the same steps. But I don't want to run into this problem in the future during kernel upgrades. Does anyone know what I missed?

9.10 uses Grub2 as default which no longer uses menu.lst.

Do a search for how to work with Grub2 or reinstall the Grub package (probably a better option).

---

### Post by ubdime on 2009-11-03
Ahhh! Much thanks. I forgot that 9.10 uses grub2.

So if I install using 9.10 cd and go through same steps to convert to raid1, further kernel updates will hopefully not have issues like this.

---

