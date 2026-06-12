---
title: "Building a new computer"
date: 2006-04-23
forum: General Help
---

### Post by enopepsoo on 2006-04-23
Sorry if this has already come up... I did a quick search and didn't think I saw it.

I will be building up a new omputer over the next month or two (to run ubuntu of course).  I was just wondering, would it be faster to install an internal flash drive (or something like that) to use as a swap partition?

I have heard that these generally fail after 100000 read/writes, so it is probably a very stupid idea.  I have just always thought that there should be some sort of memory card swap option, and with SD and whatnot being so cheap now I thought I would ask.

Thanks Ubuntuers.:D

---

### Post by sinkxdie on 2006-04-23
It wouldn't really bother me that much if it had 100,000 read/writes.
If you use it once a day, thats like 30 years with the same drive. I don't think you'll be using that same computer for 30 years. Even 3 times a day, which you probably wont use it every day, would be 10 years. That's still a lot for one computer. I'd go with the internal flash drive.

---

### Post by Golden Warrior on 2006-04-23
How much RAM will the new system have?

I have Ubuntu running on my Laptop with 512MB of RAM and it almost never uses the swap partician.  On my desktop with 1024MB of RAM it never needs to use it.

If you go with 1GB or more RAM you'll hardly even need a swap partician so I'd just use your regular hard drive for it.  If anything, if you have two hard drives in your system, you can use your first drive for running Ubuntu and use some space on the second drive for your swap so the system will be able to use it (if need be) and load programs without waiting for one drive to do it.

Besides I think it would be cheaper to go with more RAM than an internal flash drive.

---

### Post by enopepsoo on 2006-04-23
[QUOTE=Golden Warrior]
If you go with 1GB or more RAM you'll hardly even need a swap partician so I'd just use your regular hard drive for it.  If anything, if you have two hard drives in your system, you can use your first drive for running Ubuntu and use some space on the second drive for your swap so the system will be able to use it (if need be) and load programs without waiting for one drive to do it.
[/QUOTE]

I am thinking 2-3 GB RAM.  By the way, 2GB SD card is $70 at a local computer shop here compayed to $80 per gig ram.  (This is in Toronto and Canadian dollars).

I have kindof decided against doing this I guess, but would this actually be faster than using hard drive?  What if you installed the OS on this partition or something?

---

### Post by wylfing on 2006-04-23
I fully agree with **Golden Warrior**. I have 1 GiB of RAM on my desktop as well, and my swap partition is never touched. It is configured for 700 MiB but it's always unused. Considering 1 GiB of RAM sells for about $70 there is really no reason not to get it when you're putting a new box together. (Although at the low price point be prepared to get a bad stick once in a while. That's a great use for the "test memory" function of the Live CD.)

Go ahead and spare a gigabyte of disk space on your 250 GiB drive for a swap partition. You won't miss it, it'll never (or extremely rarely) be used, and so it cannot possibly slow down your system.

If you are performance-minded, focus on bandwidth -- especially video bandwidth, as things like OpenGL accelerated desktops are going to be here pretty soon. I've had systems with pretty good clock speeds feel slow because their bus wasn't up to the task of moving enough information around.

HTH

edit:

> would this actually be faster than using hard drive

No. You won't be seeing real gains here. If you're using SATA the gains will be so small that they'd be hard to measure.

---

