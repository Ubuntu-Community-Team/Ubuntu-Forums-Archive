---
title: "How do I change boot loaders?"
date: 2012-09-02
forum: General Help
---

### Post by MutantJohn on 2012-09-02
So I installed Gamedrift Linux on /dev/sdb (2nd HDD) and while I was installing, it asked me what HDD I wanted to choose for the boot loader.

Not understanding what that was because I'm convinced CS people just make words up and don't understand language as well as I do, I chose /dev/sdb so now every time I start-up, it loads from /dev/sdb first which means the grub menu puts the Gamedrift kernel above the others meaning I have a timed window to select another kernel before automatically booting into Gamedrift which is very inconvenient for me.

So how do I shift my boot loader back to /dev/sda?

Or am I asking entirely the wrong questions...?

---

### Post by imachavel on 2012-09-02
boot to the live cd. Once the desktop loads, you go to the menu and search for boot-repair. When it shows up, you can create a boot info summary and upload it to this forum in your next post. But the thing is, it's probably going to create a grub summary of the partitions of your booted live cd, which probably won't be dev/sda1 dev/sda2 or dev/sdb

or if so, it will be the partitions the way the computer sees your booted live cd. Anyway, choose repair boot, and the mbr of your ubuntu OS on the storage drive will probably be restored. Next time, understand this. Always keep the boot loader as the first partition on the first device you plan to often boot to. If you want to chose different, chose a different drive to boot to at start up by changing the boot sequence in the bios. Also allow grub to select the OS with mbr at grub. Or you can select it yourself at grub

if repairing grub doesn't fix your problem, then there probably isn't a mbr problem, but just that you chose a different device to boot to from the bios. If you remove the external hdd, will your computer boot to the hard drive automatically??

---

### Post by Bashing-om on 2012-09-03
--john;

how bout editing your config file ?
Here is a howto to select the os boot order.
[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

other links in this link --anything about grub !

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by YannBuntu on 2012-09-04
Hello
I don't know if Boot-Repair is pre-installed in the Gamedrift Linux CD.
In case it is not, see [https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

---

### Post by MutantJohn on 2012-09-04
Thank you for all the replies. Now that I have all this information, the real accomplishment will be me finally getting off my lazy butt to fix this. I will mark this thread as solved though.

---

