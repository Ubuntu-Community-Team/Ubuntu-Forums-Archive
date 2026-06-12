---
title: "Can't Boot Karmic Koala."
date: 2009-12-12
forum: General Help
---

### Post by elbandito on 2009-12-12
So a few weeks ago, Ubuntu 9.10 told me that there were some updates to install and like a good boy, I did what was asked. Everything was fine after that... until I turned off my computer. The next time I turned it on and tried to boot into Linux, it refused to go past the boot menu (normal, recovery mode, etc), saying that it can't find /root.

Details: 
I'm running a dual boot system with XP on one side, Karmic Koala on the other. I installed 9.10 from a torrent and not from a disc, declining to create a recovery CD at the time. Everything was working perfectly until the update.

XP boots fine but I'd sure love to get Ubuntu back. I'll write down the error msg and type it here. ANy help would be greatly appreciated... I've been wandering around online for the last couple of weeks and have found nothing helpful.

---

### Post by elbandito on 2009-12-12
So at the GRUB 1.97~ beta 4 menu I see:

Linux 2.6.31-14-generic
Linux 2.6.31-14-generic (recovery mode)
Win XP Media Edition (on /dev/sda1)
Win NT (on /dev/sda2)
Microsoft Win XP Embedded (on /dev/sda3)

I then choose the first option (Linux generic) and it begins to try to boot. After about 3 seconds, it says:

[1.348250] kernel panic - not syncing: VFS: unable to mount root fs on unknown - block (0.0)

I have no idea what's going on here. HELP!!

---

### Post by aot2002 on 2009-12-12
It's saying your partition doesn't exist?
Run the live cd and run the command

fdisk -l and verify your linux partitions exist and write down where they are so you can change the boot menu to them.

---

### Post by elbandito on 2009-12-12
> **aot2002 said:**
> It's saying your partition doesn't exist?
Run the live cd and run the command

fdisk -l and verify your linux partitions exist and write down where they are so you can change the boot menu to them.
I just tried this at the GRUB command line and it says that no such command exists... :S

---

### Post by FreezWay on 2009-12-12
no, he means insert the ubuntu cd and open a terminal and then run the command.

---

### Post by elbandito on 2009-12-12
In my first post, I mentioned that I installed from a torrent and declined to make a CD at the prompt and as such, don't have any such thing. Where can I find an ISO or something so that I can make one? Is there nothing that I can do from within Grub?

---

### Post by FreezWay on 2009-12-12
within grub - not that i know of. I recommend grabbing a puppy Linux cd if u have slower internet (100MB vs 700MB) there are ways to set up a flash drive too, but im not sure about how exactly. I keep a puppy cd around for these exact reasons (i have had 3 kernel panics)

puppy dl page - [http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

ubuntu dl page - [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by elbandito on 2009-12-12
Tried booting Puppy from a flash drive and got no results. :(

---

### Post by ranch hand on 2009-12-12
You can down load the LiveCD from Win JerryLewis Pro.  Just make sure you have a burning program that will burn an ISO.

Use these instructions to recover grub;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the instructions about file editing.  You need the "update-grub" and "grub-install /dev/<your drive>".

---

