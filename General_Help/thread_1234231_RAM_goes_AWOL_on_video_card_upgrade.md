---
title: "RAM goes AWOL on video card upgrade"
date: 2009-08-07
forum: General Help
---

### Post by doundounba on 2009-08-07
Hi all,

So I have a weird problem that I hope someone has either seen before or that someone (even better) has a workaround/fix for.

I am running Kubuntu 8.04.3LTS all patched up and up to date - as up to date as that release can be anyway.  I am running with 4gb of RAM and until recently was running an Nvidia 7600GS video card with 256MB DDR2 memory.  I recently upgraded the video card to a 9600GT with 1GB of DDR3 memory.  Today, I noticed something odd in my memory monitor - it only showed me as having 2.5gb of memory!

This is what free -m showed:
```
pascal@djaa:~/software/cxgames$ free -m
             total       used       free     shared    buffers     cached
Mem:          2521       1119       1402          0         24        418
-/+ buffers/cache:        676       1845
Swap:         5938          0       5938
pascal@djaa:~/software/cxgames$
```

Even though dmesg seemed to indicate that the machine is aware it has 4gb of memory:
```

[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

```

I thought of hardware failure, so I ran a full memtest successfully. I booted with a 64-bit livecd and it saw all my memory.  So I tried to put my old video card back in and reboot, and, presto:
```

pascal@djaa:~/software/iso$ free -m
             total       used       free     shared    buffers     cached
Mem:          3289       1587       1701          0        800        358
-/+ buffers/cache:        428       2861
Swap:         5938          0       5938
pascal@djaa:~/software/iso$ uname -a
Linux djaa 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686 GNU/Linux
pascal@djaa:~/software/iso$

```

My memory's back (at least as much as a 32-bit OS can see of 4gb of RAM)!

So, my question is: is there anyway I can install my 1GB video card and not lose a bunch of RAM?  Has anyone ever seen anything like this?

Thanks in advance for any help/tips/advice...

[EDIT: Should probably have prefixed this thread with "all variants"...]

---

### Post by XCan on 2009-08-07
Thing is that you only have 32 bit of address space, in there your ram will occupy most of the address, however, other stuff like your graphics card will need to reside in the 32 bit space as well. Thus, if you install a graphics card with more memory, it will bump down the total usable space. You could enable PAE which will give you enough address space for you. But I think the easiest and safest for you is simply to install Ubuntu 64 bit. The reinstallation is quite painless if you backup your home dir and your apt settings.

---

### Post by dcstar on 2009-08-07
> **XCan said:**
> Thing is that you only have 32 bit of address space, in there your ram will occupy most of the address, however, other stuff like your graphics card will need to reside in the 32 bit space as well. Thus, if you install a graphics card with more memory, it will bump down the total usable space. You could enable PAE which will give you enough address space for you. But I think the easiest and safest for you is simply to install Ubuntu 64 bit. The reinstallation is quite painless if you backup your home dir and your apt settings.

+1, if you have 64-bit hardware then use it to its capabilities with a 64-bit OS.

---

### Post by doundounba on 2009-08-10
Thanks to both of you for the feedback.  I must say I'm a bit surprised that video memory must be (partially?) mapped onto main memory... Losing ~700mb of RAM because I gained about the same amount of video memory seems odd.

Anyway, so it looks like a 64bit install is in my not too distant future. KDE4's less-than-ideal state is what has kept me on Hardy, but that release will soon be EOL'ed and KDE4.3 seems promising, so maybe it's time to make the jump.  But I must say that a re-install doesn't seem as easy as you claim, XCan.  I've been tweaking this system this way and that for a long time, and I don't think it will be trivial to get the new system to the same level of "fit"...

Anyhow, thanks again.

---

### Post by mcduck on 2009-08-10
Video memory isn't actually mapped into RAM, It's just using the same address space together with your RAM. The limit of possible memory addresses includes both RAM and video memory. So adding a graphics card that has more memory didn't result in part of your RAM being used, but the amount of total memory in your system growing higher than what the system can address.

---

### Post by doundounba on 2009-08-10
Ah, thanks mcduck, that makes sense.  I just wish I could (for the time being) tell Ubuntu to penalize the video card rather than main memory...

Also, [this Ask Dan article]("http://www.dansdata.com/askdan00015.htm") seems like a good reference on the topic. Maybe I'll also try to see if my BIOS provides any options here...

---

