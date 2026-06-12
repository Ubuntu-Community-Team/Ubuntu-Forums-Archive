---
title: "Kernel panic after updated"
date: 2009-12-18
forum: General Help
---

### Post by AmiableAdder on 2009-12-18
Ok, well I have 9.10 and it's been updated a few times. This last time it went from Ubuntu, Linux 2.6.31-15-generic to Linux 2.6.31-16-generic.

For some reason when I boot 16, it says [COLOR=Red][1.345740] Kernel Panic - Not syncing : VFS : Unable to mount root fs on unknown - block (8,3)[/COLOR]

So I went into 16's recovery mode and it came up with (these are just the things I thought looked like problems. There were a lot of other lines, but they sounded normal) :

[COLOR=Red][1.371491] Kernel Panic - Not syncing : VFS : Unable to mount root fs on unknown - block (8,3)[/COLOR]

[COLOR=Red][1.37224] No filesystem could mount root[/COLOR]   (shows root extensions it tried)

[COLOR=Red][1.354809] RAMDISK : Couldn't find valid RAM disk image starting at 0[/COLOR]




Anyone know why it would do this, or how to fix it? When I boot from 15 it works just fine (I'm using it right now), but 16 won't even start. Is there a way to erase the updates and then re-install them (could have been an install problem?)?

---

### Post by Skeena on 2009-12-24
I have a machine running Ubuntu via Wubi, and I have the same post-update problem, right down to the block (8,3). If I boot using 2.6.31-14-generic, all is fine. I've also noted another thread with a similar complaint, with the block being (8,1). In that case, the problem also emerged immediately after a recent update. 

For the time being, I'm just going to use the earlier kernel until I update again. Then I'll test again.

Anyone else having this problem? any solutions? and is there a security risk involved in using the older kernel version?

Thanks in advance.

---

### Post by AsianSpanker on 2009-12-26
Last night I updated. This morning start I have 2. 199362 kernel panic-not syncing:vfs: Unable to mount root fs on unknown block. (op) ..

I see others got the same thing from the recent update! Have we been attacked?

---

### Post by AsianSpanker on 2009-12-30
> **AmiableAdder said:**
> Ok, well I have 9.10 and it's been updated a few times. This last time it went from Ubuntu, Linux 2.6.31-15-generic to Linux 2.6.31-16-generic.

For some reason when I boot 16, it says [COLOR=Red][1.345740] Kernel Panic - Not syncing : VFS : Unable to mount root fs on unknown - block (8,3)[/COLOR]

So I went into 16's recovery mode and it came up with (these are just the things I thought looked like problems. There were a lot of other lines, but they sounded normal) :

[COLOR=Red][1.371491] Kernel Panic - Not syncing : VFS : Unable to mount root fs on unknown - block (8,3)[/COLOR]

[COLOR=Red][1.37224] No filesystem could mount root[/COLOR]   (shows root extensions it tried)

[COLOR=Red][1.354809] RAMDISK : Couldn't find valid RAM disk image starting at 0[/COLOR]




Anyone know why it would do this, or how to fix it? When I boot from 15 it works just fine (I'm using it right now), but 16 won't even start. Is there a way to erase the updates and then re-install them (could have been an install problem?)?

Did anyone reply personally that I can't see? My computer has been down for awhile and I have no idea as the steps to fix it.
[2.199098]kernel panic:VFS: Unable to mount root fs on unknown - block (0,0)..
This started happening after I allowed upgrades.

I don't understand terms like shift-a-boot or how to boot from 15 or 16. I bought all the Linux books and not one addresses such things. Is there anyway I can get a more understandable answer? I am not a computer tech, I just want to be on board with Ubuntu. Thank god I have more than one computer. But big computer Dell Dimension 9100 hasn't worked for a long time, will not boot up from a disk, and I have no idea how to do this except to wipe it and loose tons of stuff. I bought two hard drive back-ups but one has to click and copy each file to them.
Not the "automatic backup" that I thought. 

Using Ubuntu 9.10 and got kernel panic after the last set of updates. Now I try the 9.10 install disk, and I can't get that to work either. 
I thought I could remove my data by running the computer from the disk, but it goes right back to kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(0,0)..

Anybody???

---

### Post by viwiz on 2010-01-02
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all)

Go to this thread and #90 will have an attachment named wubildr that you will need to download. Use this file to replace the one that is in C:\ and then Ubuntu will boot properly again.

I tried to attach that same file here but it wouldn't allow me to, for whatever reason.

This fix worked for me and it a simple one-step deal that didn't necessitate copying lots of codes.

---

