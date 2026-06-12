---
title: "Rule of Thumb for Swap"
date: 2011-06-29
forum: General Help
---

### Post by DeathByLinux on 2011-06-29
Hello,
         I am installing Ubuntu on a friend's system and I was wondering what is the general rule of thumb for how much I should allocate for the swap partition? 
-DeathbyLinux

---

### Post by aeiah on 2011-06-29
it used to be 2.5 times the ram, or something. nowadays swap isnt that necessary at all on modern systems, but you still should have at least the same amount of swap as ram if you wish to use the hibernate function, since it offloads all ram contents to swap for this and will cause problems if swap fills up.

---

### Post by Bachstelze on 2011-06-29
What aeiah said. On modern systems, I generally put 512MB just to be sure since I never use hibernation. It's plenty but hey, diskspace is cheap nowadays.

---

### Post by nzjethro on 2011-06-29
I heard about 2-3 times the size of your RAM from a number of guides, so 2.5 times sounds about right. Another option, which may be more modular, is to post-install create a swap file, rather than creating a swap partition during your install. This way, you can run the system for a while without swap, and see what you think. Then if you want to add swap, you can add the amount you want, and if that's not enough, add more later. I created a 2GB swap file (for 2GB of RAM), using [this Ubuntu Guide]("https://help.ubuntu.com/community/SwapFaq") and have my system running well (plus I know if I add more RAM later I can up the amount of swap).

---

### Post by bryanl on 2011-06-29
In modern systems with a couple of GB of RAM or more, setting the swap size to RAM size is usually good enough. 

Whether you really need swap space any more is the question. For power state saving, being able to write RAM to disk is needed. Otherwise, you'd be hard pressed to need swap space for typical end user machines.

From what I can tell, you'd really need to get into some heavy computing to put stress on swapping and, if you are in that camp, you'll probably have a lot of RAM as well as the knowhow to set a swap for your use.

For me, if I see swap being used ('sudo swapon -s' or any of many monitors), I know something has gone wacko and its time to figure out what messed up. And I only use 2 GB or 4 GB RAM.

I also use a swap file rather than a separate partition. Since the modern kernels can use the file as easily as a partition, I don't know why Ubuntu doesn't do that by default. -- but there are a lot of things I don't know so take anything I offer with due caution only!

---

### Post by dFlyer on 2011-06-29
Everyones answer is going to be different. Why not let the software decide this for you, that is unless your manually setting up your partitions. When I setup my wifes system, I let the software do all the thinking and it produced a swap file twice the size of her ram.

---

### Post by WorMzy on 2011-06-29
There is no rule of thumb anymore, it all depends on what you're going to use the PC for, and how much RAM you have. If you have 4GB of RAM, are only going to use the PC for general web browsing and text editing, then having a 12GB swap partition is completely pointless. Then again, if you only have 512MB of RAM, and are planning on running video editing software while creating a 2000x2000 image in the GIMP, without a swap partition, you're going to have problems. Set aside as much space as *you* need for swap.

---

### Post by Herman on 2011-06-29
I don't make a separate swap area anymore, I install without one and ignore the reminder messages in the installer. After the installatiion I install 'Dynamic Swap Space Manager' from the Ubuntu Software Center, (if you can't find it, enable more sources).
I think 'Dynamic Swap Space Manager' is great, it makes a swap file in the / partition and automatically adjusts the sizes of the swap file on demand. That saves a lot of wasted space if space is an issue. especially in USB flash or small SSD installs.
I haven't run any benchmarking software to test it for performance, but I haven't noticed any performance hit so far. Dynamic Swap Space Manger and seems to work well, I think more of us should use it. :)

---

