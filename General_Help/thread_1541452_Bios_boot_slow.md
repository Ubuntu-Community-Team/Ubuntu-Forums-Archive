---
title: "Bios boot slow"
date: 2010-07-29
forum: General Help
---

### Post by floorish on 2010-07-29
When I restart from Ubuntu, the bios booting is slow (~30 sec). 

System:
HP XW4300
Dual boot XP/LUCID
Quick boot is on

If XP is restarted, bios takes about 4 seconds to get to grub, but if the last used OS is Ubuntu it takes a lot longer.  It doesn't matter whether the pc is shut down, or simply restarted. When Ubuntu is the last used OS, the bios shows '2048 mb' after ~25 seconds, XP doesn't show that. Both show some bios system info on screen.

Timeline:
XP -> restart/shutdown+start -> bios (system info, 4s) -> grub
Ubuntu -> restart/shutdown+start -> bios (nothing, 25s; '2048mb', 1s; system info, 4s) -> grub

Recent changes (after setting up dual boot):
Added ram 2048mb
updated bios firmware (1.11 -> 1.12 only security update)


I don't think the recent changes could be the problem, because in XP it is still fast, so I hope anyone of you can give me some info,
Thanks in advance

---

### Post by floorish on 2010-08-03
No one knows :(
I'm wasting 20 second of my life every day, that's .... *math* .... more than 2 hours a year! :p

---

### Post by JBAlaska on 2010-08-03
I've seen cases where exiting from Linux left the disk in a unclean state, therefore when restarting Linux it runs FSCK before booting. Might want to check that out.

Edit: strike that, I reread your post and it seems that the delay is in your bios post (Before grub), How many hard drives do you have and do you have a disk in your cd/dvd/bluray player?

---

### Post by prodigy_ on 2010-08-03
For me, restarting Ubuntu always forces a memory test in BIOS, while restarting Windows doesn't. And memory test takes some time, though 20 seconds difference is a bit too much. Unless it's very slow memory.

---

### Post by floorish on 2010-08-03
Well it's 2x 1024 MB 667MHz, just a month old so I guess they're not the slowest. I don't think it's fsck either, that takes a lot longer I think, and it's running after bios boot, isn't it?

So it does *something* with the memory (because it shows '2048MB', while XP doesn't), but no clue so far what exactly...

I appreciate your comments! :D

---

### Post by floorish on 2010-08-04
> **JBAlaska said:**
> I've seen cases where exiting from Linux left the disk in a unclean state, therefore when restarting Linux it runs FSCK before booting. Might want to check that out.

Edit: strike that, I reread your post and it seems that the delay is in your bios post (Before grub), How many hard drives do you have and do you have a disk in your cd/dvd/bluray player?


I just noticed your edit, so here we go:

Harddrives (partitions):
1) 160GB (80GB NTFS, 40GB NTFS, 19GB ext4, 19GB ext4, 2GB swap)
2) 320GB (320GB NTFS)

First two NTFS partitions both got XP installed, the ext4 partitions are for / and /home respectively.
There are no disks in the cd/dvd drives.

---

### Post by filip007 on 2010-08-04
BIOS slow boot, than is your system fault not Ubuntu. Try disable Quick boot...i don't think that your system uses EFI but who knows, your system is workstation so... 

[http://www.hp.com/workstations/pws/xw4300/xw4300.pdf](http://www.hp.com/workstations/pws/xw4300/xw4300.pdf)

---

### Post by floorish on 2010-08-04
> **filip007 said:**
> BIOS slow boot, than is your system fault not Ubuntu. Try disable Quick boot...i don't think that your system uses EFI but who knows, your system is workstation so... 

[http://www.hp.com/workstations/pws/xw4300/xw4300.pdf](http://www.hp.com/workstations/pws/xw4300/xw4300.pdf)

But Ubuntu definitely has something to do with it, how would you explain that a reboot from XP (on the very same system) is faster?
If I disable quickboot it actively checks the available memory, which takes about two more minutes, so that's not the problem.

Not 100% sure, but I don't think the system uses EFI. Any idea how I can check that?

---

### Post by floorish on 2010-08-24
Here are two other scenarios:

restart from any OS -> load grub -> press [ctrl-alt-delete] for reboot -> *no waiting*
restart from any OS -> go into bios config -> close bios without saving changes -> *20 seconds waiting*

I downgraded BIOS from 1.12 -> 1.11, but no luck.

So I guess it has something to do with a forced memory check like prodigy_ said earlier, but any clues if I can force switch the forced check off?

---

