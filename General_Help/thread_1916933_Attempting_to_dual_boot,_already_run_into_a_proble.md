---
title: "Attempting to dual boot, already run into a problem with partioning"
date: 2012-01-29
forum: General Help
---

### Post by coldjeanz on 2012-01-29
I have decided to dual boot my Win7 with Ubuntu 11.10.

I'm trying to follow this tutorial since it was very straight forward: [http://www.youtube.com/watch?v=FmN4Pj3VWpc](http://www.youtube.com/watch?v=FmN4Pj3VWpc)

I'm at the step where I need to shrink my hard drive but I'm getting this problem:

[img]http://i.imgur.com/0UqAc.jpg[/img]

I don't exactly know what that means but I can't do anything here. I currently have about 190 GB of space available on a 500 GB hard drive but it's not letting me shrink it.

---

### Post by sanscents on 2012-01-29
Well, it mentions defrag and immovable objects.  Did you run defrag in Windows before trying to partition?

---

### Post by 2F4U on 2012-01-29
The thing is that those 190 GB are not allocated contiguously on the harddrive, they are rather spread out within the  the existing partition. If you run defrag chances are that the space allocation is more contiguous. At the moment there are files towards the end of the partition and thats why you are not allowed to shrink it, since the shrink would not rearrange those files.

---

### Post by coldjeanz on 2012-01-29
i ran a defrag using the built in defragger with Windows and when I tried to shrink again it still is only giving me a maximum of like 86 GB to use. what else can I do to get more space?

edit:

i just read this on here: [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

> There are some limitations and caveats involved with using Windows own Disk Manager to shrink Windows.
For one it requires defragmenting the drive first, and defragging usually takes a lot of extra time.
Secondly and probably worse, the Windows MFT and page files show up as 'immovable files' which the Windows Disk Manager can't deal with. The most you can possibly shrink Windows is half way, (where you bump into the MFT), and that's only if you're lucky enough not to run into stray fragments of page file first.
Thirdly there's also a risk is your hard disk might fail to be recognized by the Ubuntu installer and not appear in the list of disks it's possible to install Ubuntu in. 

---

### Post by coldjeanz on 2012-01-29
if i just use the built in partition slider with the Ubuntu CD, will I also run into this problem or will it let me have access to the full 190 free GB?

---

### Post by Elfy on 2012-01-29
> **coldjeanz said:**
> if i just use the built in partition slider with the Ubuntu CD, will I also run into this problem or will it let me have access to the full 190 free GB?

An immovable file will still be immovable.

In the past when I still used windows - this was before vista - I turned off the pagefile in windows - then defragged, then resized, then turned the pagefile back on. This way the immovable file does get moved - it gets moved to a new position in the resized partition. 

I wouldn't do the resizing (don't create any partition though) of a win7 system with the partition tools on the livecd I would use the disk management tools available in windows - you might not get issues using gparted - but others here have done in the past. The gparted/installer on the livecd will see the unallocated space and use it when prompted

---

### Post by coldjeanz on 2012-01-29
Not sure what pagefile is but do you suggest I turn it off and redo all those steps if I'm using Windows 7? How do I turn it off? Thanks

---

### Post by Elfy on 2012-01-29
[http://www.racedepartment.com/forum/threads/windows-7-virtual-memory-performance-optimization.14645/](http://www.racedepartment.com/forum/threads/windows-7-virtual-memory-performance-optimization.14645/)

It's on that page - though I have no idea if the options are the same still in win7 - have a look.

So if it was me I would

turn off pagefile
reboot
defrag
resize 
turn pagefile back on
reboot 
reboot into livecd and install

---

### Post by coldjeanz on 2012-01-29
No luck. Turned off pagefile, restarted, defragged again, restarted again, and when I went to shrink it still is saying I only do a maximum of like 86000 MB. Thinking I just should settle for that now...this is taking too much time.

---

### Post by sanscents on 2012-01-29
> **coldjeanz said:**
> No luck. Turned off pagefile, restarted, defragged again, restarted again, and when I went to shrink it still is saying I only do a maximum of like 86000 MB. Thinking I just should settle for that now...this is taking too much time.

I think 86GB is lots for Ubuntu, and you can always keep file on the Windows patition.  I'll likely give my next Ubuntu install the minimum, I think I've seen 10GB, but I won't be that stingy.  The rest of the HD will be NTSF so Windows can see all my Home files.

This is related: [http://forums.techarena.in/operating-systems/1241534.htm](http://forums.techarena.in/operating-systems/1241534.htm)

---

### Post by coldjeanz on 2012-01-29
You're probably right. I know that using wubi I could access all my Windows files from the host folder. Is it similar with a real dual boot?

Also I'm sort of confused by something. It says I can shrink by a maximum of 86 GB right? So do I enter in 86000 or do I enter in 0? And actually I need to leave some space for swap correct so I probably shouldn't use all 86 GB.

---

### Post by sanscents on 2012-01-29
I've never used Wubi.  Are you on a laptop or PC?  I don't really dual-boot anymore either, rather I have two sata drives, one Win7 one Linux, and pick boot at the BIOS, if thats correct.  It's very conveinent for me, not having to deal with partitioning or MBR.  Changing OS takes a little longer maybe, but it's simple and doesn't require much computer juice to run.

---

### Post by Quackers on 2012-01-29
Leave the 86000MB in place.
By the way, make sure that you don't already have 4 PRIMARY partitions on the hard drive. This is the maximum allowed on an MBR partitioned system. DO NOT EXCEED 4, or attempt to! The consequences can be quite a pain.

---

