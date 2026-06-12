---
title: "Read only filesystem. Partitioning just hangs. I think I borked it finally."
date: 2009-08-26
forum: General Help
---

### Post by rootless on 2009-08-26
Alright, I've got a weird problem for you. Whenever I boot my Ubuntu Hardy desktop, everything works fine... until I startx from command line to start gnome.

At that point, my desktop boots, and everything seems to be doing alright, responsive, etc, except my system monitor is telling me that my processor is always at 100% usage, and as soon as I click on something, the system becomes completely unresponsive.

I do not believe that this is a processor problem- I can do everything fine from the command line. At first, I thought it was perhaps a hard drive thing, because if I start X and go back to the CLI I can see the system throwing errors at me that read DDY.. I cant remember the rest, because now I can't replicate it.

I tried to repartition my drive from a livecd and just install a new / assuming it was some sort of software bug (I had just installed vinagre and openssh). But Gparted just hung without doing anything at all for about an hour to an hour and a half before I got sick of it and cancelled.

I think this made the problem worse- now I'm getting errors about how my filesystem is read-only when I try to boot.

What the HECK? Can someone please help me?

---

### Post by cariboo on 2009-08-26
Boot from the Live CD and run fsck on your / partition. This wouldn't fix your cpu usage problem, but it should let you back in to the system.

---

### Post by rootless on 2009-08-26
Alright, I've been doing this now, hitting y every minute for about an hour. It seems that there are hundreds of errors in this partition.

---

### Post by rootless on 2009-08-26
OK, it worked, now I can reproduce the error. I'm throwing a few different ones actually.

```
[various changing numbers] ata1.01: status: {DRDY ERR}
[various changing numbers] ata1.01 ERROR: {unc}
[various changing numbers] ata1.01 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[various changing numbers] ata1.01 cmd c8/00:08:5f:99:e5/00:00:00:00:00/f0 tag 0 dma 4069 in

```

and then it repeats. It looks like the kernel thinks that this is a hardware problem because it mentions ata, right? But since I can actually access my files and use the system just fine (as long as it's not from X) I would think that this is not the case.

What do you think?

---

### Post by rootless on 2009-08-28
Alright this looks dead, I'll start a new thread for this separate glitch relating to the processor and mark this one as fixed.

---

