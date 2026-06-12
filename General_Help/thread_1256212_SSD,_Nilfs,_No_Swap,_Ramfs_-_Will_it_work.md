---
title: "SSD, Nilfs, No Swap, Ramfs - Will it work ?"
date: 2009-09-02
forum: General Help
---

### Post by hiddenh on 2009-09-02
Recieving a new Intel SSD 80GB (G2)

So i figured i would finally change my main computer(desktop) over to Ubuntu.

So couple of questions.

1.
I currently have 4gb ram.  I will not be hibernating nor using any VM.  Are there any strong arguments against not having SWAP if i dont mind the possible data loss from the kernel shutting down a program reqesting unavailable memory ?
If it turns out unstable i figure i can always add swap later.

2.
As i understand NILFS is currently the most SSD optimized filesystem. Other that the possibility of data loss are there any strong arguments against using it on a SSD.  Or is there a better file system to use for a SSD ?

3.
I plan to use ramfs to create a partition for temporary disk caching. 

Using all these together i think writes to the SSD would be minimal and speed would be optimal.  However i still have a far way to go with Ubuntu so i wanted to ask others first.

---

### Post by kidders on 2009-09-03
Hi there,

> **hiddenh said:**
> I currently have 4gb ram.  I will not be hibernating nor using any VM.  Are there any strong arguments against not having SWAP if i dont mind the possible data loss from the kernel shutting down a program reqesting unavailable memory ?
If it turns out unstable i figure i can always add swap later.Not really ... certainly not if you don't mind your machine buckling a little under pressure. 4GB is quite enough memory for many purposes, and given the lifespan implications unnecessary swapping might have for your SSD, this one seems like a no-brainer hehe.

> **hiddenh said:**
> As i understand NILFS is currently the most SSD optimized filesystem. Other that the possibility of data loss are there any strong arguments against using it on a SSD.  Or is there a better file system to use for a SSD ?NILFS is targeted more at mechanical disk drives than SSDs. Any performance boost to be had by using it with an SSD is purely accidental, rather than by design. There are other ways of significantly enhancing I/O performance with SSDs in Linux, such as tweaking your kernel's I/O configuration or exercising care when partitioning your disks & creating filesystems, to ensure cylinder & block boundaries fall in sensible places. Using new or uncommon filesystems exposes you to long-term filesystem maintenance issues that it would be nice to avoid. On top of that, any unusual characteristics NILFS may have could cause system instability (eg unexplained panics or crashes), where developers haven't taken proper account of them in their code.

If you *are* going to use NILFS, I would suggest that you at least keep it away from your root filesystem.

> **hiddenh said:**
> I plan to use ramfs to create a partition for temporary disk caching.That sounds like a good idea. Even on mechanical disks, doing this can boost performance and cut down on filesystem fragmentation. On an SSD (as you probably already know), you may not gain much in performance terms, and fragmentation is hardly going to hurt you very much, but you ought to be able to prevent your apps slowly pecking the disk to death.

Anyhow, I hope that's of some help.

---

### Post by HunterThomson on 2009-10-02
You should read the HowTo's on the OCZ Forums for SSD's.

[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)


Owe, there really is no problem with read/write cyclicals. You could have that drive constantly writing data at top speed to the drive for like 3 years sold or something like that before you were down to 80% capacity or something. You do the math for your drive.

---

### Post by nilfsguy on 2010-06-30
> NILFS is targeted more at mechanical disk drives than SSDs.
Come on - NILFS writes data in a continuous log mode meaning it appends continuously new data to the end of the occupied space on the HDD => if you e.g. edit a single 100MB text-file and change a single character, the bit that was changed will end at a completely different place than the rest of the file => if you have that FS on a normal HDD and you will read that file the disk heads will have to search for the pieces of the file all over the HDD making it extremely slow.
SDDs do not suffer seek times as there are no movable parts => NILFS is perfect for SSDs as it tries not to overwrite data (and lose time with the "transfer data to another cell => reset cell => write" cycle) but just appends stuff into the space that is already available. Ok, you have to be patient when the garbage collector wakes up and frees up space when the filesystem becomes full, but in the end it's still faster than ext2,3 reiserFS & Co. BtrFS is still too unstable - had once a total filesystem corruption and once half of the free space on the device jsut vanished.
Here some tests I did on a USB-stick using NILFS2 as root filesystem:
[http://www.blah-blah.ch/Mra/Nilfs2performance](http://www.blah-blah.ch/Mra/Nilfs2performance)

About the "No Swap" option you can use it as long as you're absolutely sure that you won't get near the limit of your physical RAM. If you do, your Kernel will crash. You could create a normal blank file and use that as swap - the Kernel, under the same conditions, will behave a bit more nicely.

---

### Post by kidders on 2010-06-30
> **nilfsguy said:**
> NILFS writes data in a continuous log mode meaning it appends continuously new data to the end of the occupied space on the HDDThat's exactly right. The result is lots of sequential I/O, which is what HDDs are best at. SSDs, on the other hand gain little or nothing from having data laid down sequentially. Additionally, some of the data loss-related benefits of NILFS are negated by the use of SSDs.

Naturally, there'll always be odd edge cases where the model doesn't work as effectively (eg extending a file by a single byte), but average performance is what counts.

That said, there's nothing particularly *wrong* with using NILFS on an SSD, but for most users, any gain wouldn't necessarily be worth the risks.

---

