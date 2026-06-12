---
title: "swappiness being ignored"
date: 2010-11-03
forum: General Help
---

### Post by b.schelberg on 2010-11-03
I noticed this problem when my laptop became almost unusable in spite of 4GB RAM and i7 processor. Some investigation showed approximately 1GB RAM in use, and about 1GB swap.

Eventually I discovered that to fix it I simply needed to:
sudo swapoff -a
sudo swapon -a
However, this becomes rather annoying having to do this each time I suspend and resume the laptop, which seems to cause the problem.

I also discovered the swappiness setting, and have set it to 10, and then 0, but it doesn't seem to have made any difference.

Here's some of my details:

```
$ uname -a
Linux Morpheus 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3898       1904       1993          0         32        322
-/+ buffers/cache:       1550       2347
Swap:         4766          0       4766

```
### Suspend and resume laptop:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3898       1601       2296          0         10        135
-/+ buffers/cache:       1455       2442
Swap:         4766        726       4040

$ cat /proc/sys/vm/swappiness
0

```
How could this be? The amount of memory in swap (726MB) could easily be contained in the free RAM, but it's not - even with swappiness at 0!

I set my machine up with a swap partition of approximately 5GB, following a recommendation that swap space is required to hibernate. If it weren't for that I wouldn't bother about swap at all.

(Ubuntu 10.10)

---

### Post by dcstar on 2010-11-04
> **b.schelberg said:**
> 
.........
I set my machine up with a swap partition of approximately 5GB, following a recommendation that swap space is required to hibernate. If it weren't for that I wouldn't bother about swap at all.

(Ubuntu 10.10)

Suspending <> Hibernating. **Exactly** which one are you referring to and what type of Suspend do you have set up in your BIOS?

---

### Post by wilee-nilee on 2010-11-04
Here is a link you can set the swappiness to your content.
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

---

### Post by b.schelberg on 2010-11-05
dcstar:
Yes I know that suspend != hibernate. I used the terms correctly in my post. Most of the time I suspend, occasionally (if I know my laptop will be off for a while and unplugged) I will hibernate it. I created the swap partition for the times that I hibernate, I don't expect it to be used when I suspend.

I couldn't find any suspend settings in my BIOS (InsydeH20 version F.09).

wilee-nilee:
I'm quite familiar with that thread. Please read my post more carefully. I've tried different settings of swappiness, but they seemingly have no effect.

---

### Post by dcstar on 2010-11-05
> **b.schelberg said:**
> dcstar:
Yes I know that suspend != hibernate. I used the terms correctly in my post. Most of the time I suspend, occasionally (if I know my laptop will be off for a while and unplugged) I will hibernate it. I created the swap partition for the times that I hibernate, I don't expect it to be used when I suspend.

I couldn't find any suspend settings in my BIOS (InsydeH20 version F.09).
..........

As an experiment you may want to put the swapoff & swapon commands in the suspend/resume scripts.

Usually BIOS has the choice of S1 or S3 Suspend.

---

### Post by b.schelberg on 2010-11-05
Yeah, I guess I could do that. However, the swapoff command takes some time to run, and it's not really fixing the real issue, which is why the system was using swap instead of RAM in the first place.

Anyway, I had to do a full restart yesterday to get an external monitor to configure correctly, and the problem hasn't reappeared since then.

Interestingly, though, I noticed that the amount of space for buffers in memory is now significantly higher:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3898       2998        899          0       1174        734
-/+ buffers/cache:       1089       2808
Swap:         4766          0       4766

```

---

