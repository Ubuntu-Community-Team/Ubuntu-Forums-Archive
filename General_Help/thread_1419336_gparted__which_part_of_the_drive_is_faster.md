---
title: "gparted : which part of the drive is faster?"
date: 2010-03-01
forum: General Help
---

### Post by chriskin on 2010-03-01
i have read some time ago the the outer parts of a drive are faster
on gparted, is that the left side or the right one?

{consider this thread solved. i don't put the tag as i would like to know for future reference, but it is not actually needed anymore}
(solved on the last post)

---

### Post by azagaros on 2010-03-01
a circle has a right and left side when spinning?  I can see a top and bottom but a right and left going around and around or I change my position on the circle?

---

### Post by chriskin on 2010-03-01
if that was a "joke" , i can't find the funny part

---

### Post by azagaros on 2010-03-01
The question is do you know Physics?  And moving something along and strait line thought the center of circle...a Drive head moves in a strait line.. Which part is faster on a variable speed drive.. the data is accessed at the same rate from one edge of the platter to the other.

---

### Post by chriskin on 2010-03-01
i just have to report that you are , without reason, destroying a thread where i Really need some help

---

### Post by azagaros on 2010-03-01
gParted the partition manager of Gtk/Gnome.  Resizing a partition is all dependent on the access of the drive.  Which I describe above.  Being faster at one point over another, might be in the algorithms of a repeating thing like read here write there..Update a partition table, which on most non-windows/os2 systems seems to take forever, so I have noted.

---

### Post by chriskin on 2010-03-01
why are you talking about things i didn't ask and why are you answering on a thread that you can't help ? (!)

please leave this topic as it is, i'm continuing with my installation no matter which partition would be faster

---

### Post by dcstar on 2010-03-01
> **chriskin said:**
> i have read some time ago the the outer parts of a drive are faster
on gparted, is that the left side or the right one?


In the "olden days" of fixed sector counts on hard disks there were no parts of a drive faster than the other, there were the same quantity of sectors per track whether on the first cylinder or the last.

With modern drives there are more sectors on the outer cylinders than the inner - the sector density varies because there is more physical space on the outside of the platter compared to the inside of the platter to fit each sector on and modern hard drive electronics takes advantage of this to maximise storage capacity.

The end result is that you can read/write more sectors per revolution on the outside of the hard disk, so that becomes "faster" for large file I/O operations. Unless you are doing large, intensive disk I/O, the benefit may still be marginal.

To answer your second question, the "faster" area in gparted is the LHS - starting from Track/Cylinder 0.

---

### Post by chriskin on 2010-03-01
> **dcstar said:**
> In the "olden days" of fixed sector counts on hard disks there were no parts of a drive faster than the other, there were the same quantity of sectors per track whether on the first cylinder or the last.

With modern drives there are more sectors on the outer cylinders than the inner - the sector density varies because there is more physical space on the outside of the platter compared to the inside of the platter to fit each sector on and modern hard drive electronics takes advantage of this to maximise storage capacity.

The end result is that you can read/write more sectors per revolution on the outside of the hard disk, so that becomes "faster" for large file I/O operations. Unless you are doing large, intensive disk I/O, the benefit may still be marginal.

To answer your second question, the "faster" area in gparted is the LHS - starting from Track/Cylinder 0.

since the benefit is marginal as you said it's ok - i have made the mistake to install the os on the right side of gparted and keep the less-used files on the left hand side.

thanks for the complete answer

---

### Post by birge on 2010-06-02
> **dcstar said:**
> In the "olden days" of fixed sector counts on hard disks there were no parts of a drive faster than the other, there were the same quantity of sectors per track whether on the first cylinder or the last.

With modern drives there are more sectors on the outer cylinders than the inner - the sector density varies because there is more physical space on the outside of the platter compared to the inside of the platter to fit each sector on and modern hard drive electronics takes advantage of this to maximise storage capacity.

The end result is that you can read/write more sectors per revolution on the outside of the hard disk, so that becomes "faster" for large file I/O operations. Unless you are doing large, intensive disk I/O, the benefit may still be marginal.

To answer your second question, the "faster" area in gparted is the LHS - starting from Track/Cylinder 0.

Fantastic answer. Thanks. I was looking for the same information. For some reason I assumed (no good reason, as it turns out) that the right hand side of the Gparted window would refer to outer cylinders. The difference in speed from the inner to the outer tracks is actually significant! Just do a full disk throughput test and you'll see. So, if the OP is still listening, it's actually worth your while to put things like the swap and tmp partitions on the outer part of the disk.

By the way, those of you who just made stupid comments to the OP should just buzz off. Especially the fool who accused the OP of not knowing physics. It is actually your ignorance that caused you to misunderstand a very simple, and completely valid question.

---

### Post by Serpher on 2010-06-02
I always thought hardrives read from the inside of the disc out...not around and therefore I thought the partitions would be divided up and down the disc, not around it. Is this the case in older hardrives or something?

---

### Post by BoneKracker on 2010-06-02
> **dcstar said:**
> In the "olden days" of fixed sector counts on hard disks there were no parts of a drive faster than the other, there were the same quantity of sectors per track whether on the first cylinder or the last.

With modern drives there are more sectors on the outer cylinders than the inner - the sector density varies because there is more physical space on the outside of the platter compared to the inside of the platter to fit each sector on and modern hard drive electronics takes advantage of this to maximise storage capacity.

The end result is that you can read/write more sectors per revolution on the outside of the hard disk, so that becomes "faster" for large file I/O operations. Unless you are doing large, intensive disk I/O, the benefit may still be marginal.

To answer your second question, the "faster" area in gparted is the LHS - starting from Track/Cylinder 0.

Good answer.  I'd just add that this is one (of several) reasons behind the traditional partitioning scheme used on many servers:

boot swap root tmp var usr home

(That's just trivia, folks; don't go repartition your machine.  The Ubuntu defaults are good.)

---

### Post by srs5694 on 2010-06-03
There's another factor that should be considered if you want to optimize partition layout for speed: seek latency. Suppose you put swap at the end of the disk, and the system begins to use swap while also accessing normal files. When this happens, the head has to move from some earlier part of the disk (where the normal files are) to the end of the disk (where swap is). Thus, although swap may be faster at the end of the disk, the overall speed may be lower than if swap were closer to whatever normal filesystem is in use, since the time to move the head (the seek latency) could more than undo any benefit from the faster swap speed.

In practice, of course, these competing factors mean that to get a definitive answer, you've got to run some very careful tests, based on *your* hardware, *your* system usage patterns, etc. In almost all cases, you'll spend more time running such tests than you could possibly save by optimizing the system.

Personally, I've stopped worrying about location on disk as a factor in speed. I try to keep related partitions clustered together, particularly in multi-boot systems. That is, I keep all the Linux partitions together, all the Windows partitions together, etc. I put shared-data partitions between the two sets of partitions. (On systems with more than two OSes, I've got to compromise on the placement of the shared-data partitions.)

---

### Post by BoneKracker on 2010-06-03
> **srs5694 said:**
> There's another factor that should be considered if you want to optimize partition layout for speed: seek latency. Suppose you put swap at the end of the disk, and the system begins to use swap while also accessing normal files. When this happens, the head has to move from some earlier part of the disk (where the normal files are) to the end of the disk (where swap is). Thus, although swap may be faster at the end of the disk, the overall speed may be lower than if swap were closer to whatever normal filesystem is in use, since the time to move the head (the seek latency) could more than undo any benefit from the faster swap speed.

In practice, of course, these competing factors mean that to get a definitive answer, you've got to run some very careful tests, based on *your* hardware, *your* system usage patterns, etc. In almost all cases, you'll spend more time running such tests than you could possibly save by optimizing the system.

Personally, I've stopped worrying about location on disk as a factor in speed. I try to keep related partitions clustered together, particularly in multi-boot systems. That is, I keep all the Linux partitions together, all the Windows partitions together, etc. I put shared-data partitions between the two sets of partitions. (On systems with more than two OSes, I've got to compromise on the placement of the shared-data partitions.)

Do you think this is really a factor still on modern drives (as of the last few years), which have native command queuing and large caches?

---

### Post by srs5694 on 2010-06-03
> **BoneKracker said:**
> Do you think this is really a factor still on modern drives (as of the last few years), which have native command queuing and large caches?

You could ask the same thing about the front-to-end performance differences. The only way to know for sure is to run some tests. I haven't seen such tests run in recent years, so AFAIK all advice on this matter is based on the received wisdom from several years ago.

---

### Post by dcstar on 2010-06-03
> **srs5694 said:**
> You could ask the same thing about the front-to-end performance differences. **The only way to know for sure is to run some tests.** I haven't seen such tests run in recent years, so AFAIK all advice on this matter is based on the received wisdom from several years ago.

Because storage technology is a never-ending moving target that highlighted advice is probably the most valid of all of our opinions.

However, having recently obtained a SSD that now boots my 10.04 system to the login screen in just a few seconds after grub kicks off the process, I can certainly advise that if you want a quick system then these things are the way to go - but don't waste them by putting a heavily used Swap resource on them, use an old-fashioned mechanical drive for that sort of grunt work.

---

### Post by BoneKracker on 2010-06-03
> **dcstar said:**
> Because storage technology is a never-ending moving target that highlighted advice is probably the most valid of all of our opinions.

However, having recently obtained a SSD that now boots my 10.04 system to the login screen in just a few seconds after grub kicks off the process, I can certainly advise that if you want a quick system then these things are the way to go - but don't waste them by putting a heavily used Swap resource on them, use an old-fashioned mechanical drive for that sort of grunt work.

I hear people worrying over strategies not to wear out their SSDs, but, not knowing much about them, I tend to think that at this early stage of that technology's life-cycle, any given device will be obsolete long before it's worn out.  Am I wrong?

---

### Post by dcstar on 2010-06-03
> **BoneKracker said:**
> I hear people worrying over strategies not to wear out their SSDs, but, not knowing much about them, I tend to think that at this early stage of that technology's life-cycle, any given device will be obsolete long before it's worn out.  Am I wrong?

Current good quality SSDs have built-in mechanisms to level the wear on the whole device so that their lives are maximised, but for something like Swap the inherent nature of that requirement will significantly ratchet up the number of Write cycles on any drive that hosts it, and that is still something I want to avoid on my SSD.

In reality it may not be a factor, but I'd rather spend a few dollars on more RAM to reduce swap use (which will significantly increase my machine's performance anyway) than 5 times as much on replacing a SSD worn out prematurely by to much Swapping.

---

