---
title: "Doubled RAM memory, no visible changes"
date: 2009-07-13
forum: General Help
---

### Post by galvao on 2009-07-13
Greetings.

I've recently doubled the RAM memory of my desktop (from 1Gb to 2Gb) and I didn't noticed any changes on KDE's performance (Kubuntu 9.04).

Are there any recommended changes I should make? Any tips on this?

TIA,

---

### Post by j7%&lt;RmUg on 2009-07-13
For a start can you list your other system specs (CPU, GPU, motherboard, etc)?

---

### Post by HavocXphere on 2009-07-13
No surprise there...

You can try preload.

Don't expect major gains though. A system with 1gb free and a system with 7gb free both perform the same. (On ubuntu at least. It's a different story w/ superfetch).

---

### Post by dave_i on 2009-07-13
Just to check - has the new RAM been recognised by your system? Try opening System Monitor and open the System tab, and it will tell you how much RAM is recognised. If the new RAM hasn't been recognised, make sure it's firmly seated in its slot.

However, the RAM may not have been the limiting factor in your system. The reason adding extra RAM speeds things up is that when the computer runs out of space for randomly-accessed data on the RAM chips, it starts writing and reading that data to/from the hard disk, which is a *lot* slower than writing/reading to/from RAM. If the system isn't running out of space on the RAM chips, then it doesn't need to write data to the hard disk and adding more RAM has no effect. 

For instance, I'm just running firefox and a couple of other small applications at the moment, and my computer's using about 650MB of RAM. At the moment, it wouldn't matter if I had 100GB of ram or 1GB RAM, the limiting factor is something else - for instance the CPU or disk input/output, or the RAM frequency.

You will notice speed improvments using software that requires more RAM.

---

### Post by Andy06 on 2009-07-13
ASSUMING your RAM has been seated correctly and is of the right type for your system, you will not see an immediate apparent difference, you WILL however see it if you try to push the limits.

Pls post you earlier and latest configuration along with RAM values.

If you had 512 MB earlier, take out the new stick to take it back to the 512MB config and then start 2-3 windows of firefox with 8-10 tabs each (with generous helpings of flash and ajax sites), then open openoffice writer and load a large document and then start playing some videos from hard disk using Mplayer or SMplayer or whatever, just to make it worse, play some music on Amarok as well. Watch your system grind to a halt.

Now stick in the new ram, and lets say you now have 2 GB, do the same things as above and the system will be faster, much much faster.

Linux does not use RAM as efficiently in some cases even with preload as Windows Vista does with Superfetch. You will notice that Vista uses upto 50% of RAM if you have 2 GB whereas Ubuntu will hover around 10%. The reason (apart from Vista being a resource hog in general) is Vista loads up your frequently used apps in RAM for quick access, this makes it noticeably faster even when you are not doing much as the loading speeds increase a lot. You can test this by doing warm and cold start tests of some heavy apps. You will see windows perform very well on the warm starts. Trade off is when windows has to swap out something to load something it did not predict, I am assuming linux would take the cake here since it won't have to perform the swap out operation. I don't really know how fast or efficiently either of them perform swap outs.

If you want a big performance boost, it would be more apparent with a better CPU with more cores, hyperthreading, faster speed (the GHz value) and larger memory cache. 

Also apart from the quantity of RAM, the speed matters too. 2 GB of RAM is just the virtual memory that it can hold, so basically 2 GB worth of info. But how fast can it access and load this info? That is (I think) determined by the RAM speed such as 667Mhz, 800MHz, 1066MHz.
You will have seen RAM listed like this: 2GB PC-8400 800Mhz or something like that. That last part is the speed.

---

### Post by TeamJ on 2009-07-13
well you just need to make sure there is enough ram. there is no point in empty ram.
the processor speed is important though
which graphics card are you using?
the Intel GMA Driver is crap and slows the system down

---

### Post by hyperdude111 on 2009-07-13
More ram does not make the system that much faster It only makes it less likely for you to run out and crash.

The most noticeable speed change would come from a cpu upgrade.

---

### Post by realzippy on 2009-07-13
Hey,
have a look at:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

...Performance tuning with ''swappiness''

The swappiness parameter controls the tendency of the kernel to move processes out of physical memory and onto the swap disk. Because disks are much slower than RAM, this can lead to slower response times for system and applications if processes are too aggressively moved out of memory.

    *

      swappiness can have a value of between 0 and 100
    *

      swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible
    *

      swappiness=100 tells the kernel to aggressively swap processes out of physical memory and move them to swap cache
    *

      Ubuntu uses a default setting of swappiness=60

Set your swappiness to 0,so more RAM will be used (instead of swap)...

---

### Post by Andy06 on 2009-07-13
Yeah, that setting really does not help much. Mainly because as it is, Ubuntu rarely rarely ever even touches the Swap. Infact the ONLY time I think I have ever used it on my system is when I hibernate.

They really should make the Swap file a dynamically resizeable system file like in Windows so that we can do away with that extra partition and remove the need for extended partitions. I doubt there are any disadvantages to it coz there is a massive thread on how to do this manually, too geeky/advanced for me though :D

Hard disk speed also makes a huge difference. So to sum up, HDD, CPU, GPU all very important even at a basic level. RAM on the other hand is like air, you don't really need or appreciate it unless you're running out or not getting any. It sort of PREVENTS you from slowing down (by opening too many apps) rather than speeding you up if that makes any sense.

Basically, this should really help you understand it:
More RAM = Smoother, faster and better MULTI TASKING. Its more important than anything else for multi-tasking.

But if you are not multi-tasking, its not so important. Then you should be looking at CPU/GPU/HDD to speed you up.

---

