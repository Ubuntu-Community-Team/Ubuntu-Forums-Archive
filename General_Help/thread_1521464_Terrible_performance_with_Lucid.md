---
title: "Terrible performance with Lucid"
date: 2010-06-30
forum: General Help
---

### Post by newio on 2010-06-30
Hey All,

Just looking to see if any one else has similar issues and work arounds.

I use kubuntu as my desktop workstation, and on it run 2 VM's in VMWare workstation (A RHEL and a Win7), Eclipse IDE, lots of terminal sessions, amarok, kopete, openoffice, firefox, chrome and a few other lil odds and ends.

On 9.04, all this worked perfectly, on 9.10, no a problem either. On 9.10, work also upgraded my laptop to a Core i7 4GB RAM.

So im quite dismayed when i try to run this on my recently upgraded Lucid setup, and the entire machine grinds to a halt with out even half of the applications i run open. It just seems to be a HUGE memory resource hog, and then the system becomes totally unresponsive as its never ending swapping begins.

Even when the system first boots, top reports the 70% of memory is being used. I know all u linux lads are going to say thats file cache and whatnot, ut then as soon as a few apps are open, it starts going into swap space (Sometimes over a gigabyte's worth) and then swaps chunks until my system is unusable.

When i first started at this company, they said i can use whatever OS i want as long as it doesn't effect my work performance... well, this is very much affecting my work performance and may end up with me back on a Windows desktop...

So rant over, anyone have any similar issues?

---

### Post by wilee-nilee on 2010-06-30
Did you upgrade the 9.10 to 10.04 in a VM?

Your description does not really get to the point, or give enough of pertinent information, like looking at the system monitor to see whats taking up all the cpu.

Also your post is a bit condescending. Ranting will get you little help.

---

### Post by newio on 2010-06-30
My post was meant to be, this is a general 'feeling' post where im looking for users with similar issues. I've used Linux for over 13 years now, if it was a problem of simple resource hogging processes, it would have been fixed and no post made here.

but, if you want some stuff to look over:

Lots of swap being used
```

free -m
             total       used       free     shared    buffers     cached
Mem:          3951       3849        101          0         16        292
-/+ buffers/cache:       3540        410
Swap:        11574        805      10769

```saidar reports lots of paging activity (I had to put my system back into the ground to get this). Notice Load Avg's are all low, despite the massive swapping activity.
```

Load 1    :   0.89   CPU Idle  :  94.49%  Running   :     1   Zombie    :     0
Load 5    :   0.95   CPU System:   1.51%  Sleeping  :   263   Total     :   264
Load 15   :   1.29   CPU User  :   3.99%  Stopped   :     0   No. Users :     1

Mem Total :   3951M  Swap Total:  11574M  Mem Used  : 97.63%  Paging in :     3854
Mem Used  :   3858M  Swap Used :    803M  Swap Used :  6.94%  Paging out:    402
Mem Free  :  95708K  Swap Free :  10771M  Total Used: 30.02%

```I'd give you a ps -ef, but all you're going to see is the applications listed above (minus some i've closed down to try and keep my system running...


*Ed, and this kubuntu install in running on the physical laptop. Its not an upgrade, its a format/reinstall (Had bad experiances with upgrades on kubuntu). The VM's are things i use for work, running on top of kubuntu in VMWare Workstation 7.2.2 (?).

---

### Post by RJARRRPCGP on 2010-06-30
> **newio said:**
> 

So im quite dismayed when i try to run this on my recently upgraded Lucid setup, and the entire machine grinds to a halt with out even half of the applications i run open. It just seems to be a HUGE memory resource hog, and then the system becomes totally unresponsive as its never ending swapping begins.

That's so not typical of Ubuntu.

It's time to wipe the HDD, repartition, reformat and reinstall. Sorry. :( 

It's recommend that you only do clean installs. I also recommend that you use Ext4.

---

### Post by wilee-nilee on 2010-06-30
Not sure but this line seems to be using everything up.
```
Load 1    :   0.89   CPU Idle  :  94.49%  Running   :     1   Zombie    :     0

```

That is strange a zombie in Linux usually is just some package still in the system and not taking up cpu.

Usually a restart or two will get rid of a zombie, but if this is persistent I would boot the live cd and see if it's running the same way. Have you been perchance running in root for any length of time?

If you have been using Linux this long I suspect you would know much more then I do.

Edit: Noticing the post above I would agree with a fresh install, you could look forever for the solution, and never really get your OS setup like a fresh install would be.

---

### Post by newio on 2010-06-30
> **RJARRRPCGP said:**
> 
It's time to wipe the HDD, repartition, reformat and reinstall. Sorry. :( .

Yeah, i did that last week to install Lucid. Maybe i should try again and just make sure i didn't install anything thats causing the issue

What about the fglrx driver, anyone having any issues with that on a Dell 1557 laptop. When i installed that, it did make the system fan get a little noisier... (weird, i know...)

---

### Post by newio on 2010-06-30
> **wilee-nilee said:**
> 
That is strange a zombie in Linux usually is just some package still in the system and not taking up cpu.


The saidar output looks fine, except for the numbers after the "Paging out" and "Paging in" section. The Zombie count is displaying 0, which is a good thing, but if not its not always a bad thing. This will explain zombie process better then i can: [http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

---

### Post by newio on 2010-06-30
Also seems it cold possibly be IO related. The system comes to a crawl with any copy operation, even when its USB-USB...

---

### Post by newio on 2010-07-07
well, solution was found. Flogged 4GB of RAM out of a new employees system to take mine up to 6GB. Now everything runs fine.

Point in case, kubuntu 10.04 is a memory hog.

```

free -m
             total       used       free     shared    buffers     cached
Mem:          5971       5920         51          0        158       2690
-/+ buffers/cache:       3071       2900
Swap:        11574         11      11563

```

---

