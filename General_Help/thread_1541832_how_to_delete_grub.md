---
title: "how to delete grub?"
date: 2010-07-29
forum: General Help
---

### Post by nerdnerd on 2010-07-29
heey everyone

I bought a new harddisk, which had already ubuntu installed. My computer is very old i figured windows 98 would be perfect.

i formatted the harddisk with the windows 98 bootcd however I could not install windows 98 because it says there is still another OS installed. As I boot now it says:
GRUB Error: Unknow filesystem
Grub Rescue>


I already formatted, what do i do?

---

### Post by oldfred on 2010-07-29
from liveCD you can install a windows boot loader:

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR


It has been so long I have forgotten but wasn't it sys c: to install the boot loader from a windows floppy?

---

### Post by nerdnerd on 2010-07-29
yes it was sys C:

but i already tried that, without success :s I really thought i was losing my mind, i didnt know what was wrong with the harddrive

but i downloaded and burned the ubuntu live cd, and load the computer from the cdrom drive

now i see a screen which says:

ubuntu
  .....


the dots are changing colors from white to red to white etc

it has been like this for 10 minutes now...

---

### Post by nerdnerd on 2010-07-29
ok guys, whats this:

the ubuntu screen stopped.
now i got this message:

```
No init found. Try passing init= bootary.
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```



help plz..

---

### Post by vandorjw on 2010-07-29
[http://www.pcmech.com/article/zero-writing-a-hard-drive/](http://www.pcmech.com/article/zero-writing-a-hard-drive/)

Follow this article instructions. It'll take quite a while...but it will work.

Cheers - CC7

PS: windows 98...really? why not windows 95, or 3.1 for that matter.
Windows 2000 (also unsupported will run equally well if not better than windows 98.)

---

### Post by Joe of loath on 2010-07-29
If you're going for a lightweight OS, go for one that you can actually download programs that work on it (Trust me, it's hard enough finding stuff that works with 2k, let alone 98...) I can't recommend puppy Linux enough.

---

### Post by nerdnerd on 2010-07-29
puppy linux? need to check that out

also im making the ultimate boot cd. im gonna try to zero write that harddisk now.
i have no idea if it will work, since fromatting didnt delete grub.
also my system said that there was some kind of compressed OS installed or something?
i cant really remember what it said exactly, but i do know something was compressed

---

### Post by oldfred on 2010-07-29
The ultimate boot CD may already have lilo installed. Many of the repair CD's have it just to fix windows boot issues.

If system was so old as to run win98 it probably does not have enough memory to run the full Ubuntu and may be slow with some of the lightweight versions of Ubuntu.

From any linux liveCD:
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1

---

### Post by nerdnerd on 2010-07-29
> **oldfred said:**
> The ultimate boot CD may already have lilo installed. Many of the repair CD's have it just to fix windows boot issues.

If system was so old as to run win98 it probably does not have enough memory to run the full Ubuntu and may be slow with some of the lightweight versions of Ubuntu.

From any linux liveCD:
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1


yeah it was actually a windows ME computer. 866 mhz, 128 mb ram. 40 gb hdd

there was a lot of dust inside, i cleaned it with a vacuum cleaner. i also screwed the processor open and its air cooled. so there was a lot of dust on the cooling pannel, i cleaned that with a toothbrush.
I blew in the computer a few times to get all the dust off the green plates.

anyway there is a lot of strange things going on with it. like sometimes it doesnt boot from cd even though i set bios to start from cd before hdd
also sometimes it will just stop working, like just yet it rebooted out of nothing and right now it seems like it is stuck in ultimate boot cd menu.
oh wait it rebooted out of nothing again and it doesnt boot from cd again.
again error: unknown filesystem. 
grub rescue

fml

---

### Post by colin.p on 2010-07-29
Could very well be a hardware issue as well. Maybe flaky ram or even a a power supply going out. I had an old K6-3 computer that I blamed on the ram, but actually what screwed the ram up was the power supply.
Interestingly, I always used no-name power supplies but this one that caused me the most problem was an Antec that cost more than the cases with the no-name power supplies. Go figure.

---

