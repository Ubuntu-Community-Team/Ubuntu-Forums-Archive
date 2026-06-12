---
title: "Making use of 2GB of RAM and Swap"
date: 2009-08-07
forum: General Help
---

### Post by nullmind on 2009-08-07
I have a notebook with **2GB** of RAM in it. I understand rather well how Linux makes use of the swap for IO caching, and I also have set vm.swappiness to 0 in an attempt to reduce swapping so that my ram can actually be used.

However, time and time again I never see real usage go over **800MB** of memory used, and typically see 1GB of swap being used.

I have been considering running a machine without any swap at all recently, since I cannot handle the slow nature of when things decide to swap, but I also understand there are a lot of problems with running a swapless machine.

Is there a existing way to not use a swap partition, and if memory goes above *x* do `swapon -a` ? In the event that my system starts using say 1.5GB of RAM I wouldn't mine having the swap enabled, but any time before that is a waste it would seem.

I'm using XFS and I don't really prefer to have the kernel doing the IO caching anyhow, since I never see real throughput from that with my desktop system.

Other than setting vm.swappiness to 0 is there a way to basically say "stop swapping!" without `swapoff`?

Thanks,
Kris

---

### Post by mikewhatever on 2009-08-07
Apparently, turning off swappiness didn't work, so I have to ask, how did you set it to 0? Have you verified it stays that way?

---

### Post by kerry_s on 2009-08-07
there's no need to mess with the memory settings, just let it do what it does & you will get the best performance. only old stuff in ram is swapped out, nothing newly started uses swap. not having swap will not increase performance, in that case old stuff is just discarded instead of swapped out for faster access.

the idea of swap is faster access to prior used stuff, it is compressed and held there incase it's needed again, other wise it will have to search the disk, load all the libs needed, then start the program, which is micro sec's longer than fetching it from swap.

windows has always done the same thing, but i'm sure you never worried about it there, so theres no need to worry about it now.

---

