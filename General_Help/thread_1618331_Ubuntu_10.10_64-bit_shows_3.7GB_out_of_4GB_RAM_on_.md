---
title: "Ubuntu 10.10 64-bit shows 3.7GB out of 4GB RAM on laptop w/dedicated graphics"
date: 2010-11-10
forum: General Help
---

### Post by UnrealMiniMe on 2010-11-10
Yes, I'm starting another one of THESE threads. ;)

**Details:**
I'm accustomed to Ubuntu showing 3.9GB out of 4GB on my desktop.  That's completely ordinary and expected:  The kernel uses a dozen megs or so, which are not accounted for in the reported memory totals.  After truncating, that brings us to 3.9GB.

I was expecting to see the same thing on my Elitebook 8740w, but System Monitor is reporting only 3.7GB instead, using the same version of Ubuntu.  free -m shows:
             total       used       free     shared    buffers     cached
Mem:          **3819**        935       2883          0         80        287
-/+ buffers/cache:        567       3252
Swap:         4095          0       4095

That is to say, the total of 3819MB is not missing a mere dozen or so MB but a full 267MB from 4096MB!  That's WAY too much to be accounted for by the kernel, so something else is going on!

Please note the following:
[LIST][*]BIOS shows the full 4GB, and so does lshw.
[*]uname -a = Linux COMPNAME 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 **x86_64** GNU/Linux
[*]lspci | grep VGA = 01:00.0 VGA compatible controller: ATI Technologies Inc Broadway XT [Mobility Radeon HD 5800 Series][/LIST]

That is to say, I really do have 4GB RAM, my mobo and BIOS recognize it, I really am running a 64-bit OS, and I really shouldn't have any kind of onboard graphics.

The devil lies in the details though:  I SHOULDN'T have any kind of onboard graphics...but the best explanation I can come up with is that 256MB or so are being set aside for that purpose anyway.  This is a mobile workstation with dedicated Firepro graphics (based on the Mobility Radeon HD 5800), and it's well beyond the range of laptops that include switchable graphics.  However, it has an i5 processor, so I think it's conceivable that the laptop is being tricked into allocating RAM for integrated graphics.  This is especially likely considering I get the same i915 error as [the threadstarter here]("http://ubuntuforums.org/showthread.php?t=1617483"), and I have very similar command line output.

**Presumed Problem:**
Long story short, I think Ubuntu is seeing the i5 processor and setting aside 256MB or so for the integrated graphics which it THINKS I have, which are actually totally unavailable to use on this particular laptop.  If this is the case, does anyone know how to make it stop doing this, so I can make that memory accessible to the rest of the system?

Of course, I could be wrong here, so entirely different explanations and solutions are welcome as well.

**Update:**
Interestingly, even Memtest is showing only 3952MB.  This may or may not account for the full missing amount, but it obviously counts for a lot.  I'm used to Memtest showing I think 4095MB on my desktop, meaning Memtest itself presumably only takes ~1MB.  Actually, even on the laptop Memtest says only 1024KB are reserved, so 143MB are totally unaccounted for.  Something strange seems to be going on...hrm...

---

### Post by krazyd on 2010-11-11
Try ```
free -mb
```

4GB = 4,000,000,000 bytes in marketing-speak.

---

### Post by dcstar on 2010-11-12
> **UnrealMiniMe said:**
> Yes, I'm starting another one of THESE threads. ;)
........

And they have been answered a thousand times now, why is this one any different?

Read what they ALL say about mapping of resources below 4GB, and then go ask the supplier of your laptop if it supports RAM over 4GB, and if it doesn't then they won't bother to increase their costs by redesigning the hardware to map things over 4GB and recover a piddling amount of RAM for the few people who care about it.

---

### Post by UnrealMiniMe on 2010-11-12
> **krazyd said:**
> Try ```
free -mb
```

4GB = 4,000,000,000 bytes in marketing-speak.

The decimal prefixes used in marketing only apply to drive storage, not to RAM.  Any and every 4GB stick of RAM really is 4096MB, or 4294967296 bytes.  Because of the way RAM works, it would probably be a lot more difficult and expensive to manufacture a stick of RAM with 4 billion bytes...or any non-power-of-two, for that matter.

> **dcstar said:**
> And they have been answered a thousand times now, why is this one any different?
There's no need for the dismissive tone.  Since I already indicated that I'm aware of the other threads, it should have been clear that I already read a good deal of them.  I did my homework.  This one is different because I already know the question has been answered a thousand times now, and I've already read those answers, and I posted this new thread because they do not apply here.  The fact that I gave so much detail in my post and headed off the usual explanations should have indicated this.

> **dcstar said:**
> Read what they ALL say about mapping of resources below 4GB, and then go ask the supplier of your laptop if it supports RAM over 4GB, and if it doesn't then they won't bother to increase their costs by redesigning the hardware to map things over 4GB and recover a piddling amount of RAM for the few people who care about it.

I'm aware of 4GB limitations on 32-bit platforms and OS's, and I'm aware of memory remapping, and I'm also aware that a motherboard chipset must be able to support over 4GB.  The snag is, my own laptop supports up to 16GB (or is it 32GB now?), so I know it's not a 4GB limitation issue.

However, running Memtest also showed me that it's not a Ubuntu/Linux issue either.  I wasn't expecting that, because I know for a fact that this laptop is capable of running at least 16GB of RAM.  After realizing it wasn't a Linux issue, I took the issue elsewhere.

For the record though, I still have no clear explanation or solution.  What I do know is that this laptop is reserving 145MB of address space for hardware, despite the fact that it supports WELL over 4GB of addressable memory.  That's according to Resource Monitor in Win 7.  Strangely, Memtest only sees 1MB of reserved memory, and the other reserved 144MB are totally unaccounted for there.  Or maybe I should say that 143MB are unaccounted for, since either Memtest is rounding cached memory down to 3952MB, or Win7 is rounding hardware-reserved memory up to 145MB.  (The rest of the "missing" memory in Linux is apparently just going to the kernel.  That amount seems a bit higher than I'm used to, but it is what it is.)

Anyway, from my understanding of memory remapping and 64-bit addressability, this should not be happening.  If my mobo/BIOS is remapping memory, Memtest at the very least should be able to account for all 4GB, and almost all of that should be in the cached category.  If my memory is NOT being remapped, my 1GB of video RAM should be taking up an enormous amount of address space too, leaving me with far less accessible RAM than I have right now.  Basically, neither possibility readily explains what's going on, and I have not yet found a satisfactory answer.  My best guess at this point is that the memory remapping implementation in BIOS is half-assed and broken, and only my graphics card is getting remapped to higher addresses to not overlap with system RAM.  Either that, or something is literally using the RAM itself, not just the address space.

---

