---
title: "How does Ubuntu utilize quad-core?"
date: 2012-07-19
forum: General Help
---

### Post by Kols on 2012-07-19
I'm running Precice 64-bit on Intel Core i5 750 on a Asus P755D motherboard.

I'm wondering how Ubuntu utilizes my CPU. Reason for this is, that whenever I'm running something which requires a bit of calculating power, it seems that core 0 (or the first core, if you prefer it) takes all the load, whereas the other 3 stays pretty much idle (2-8 %).

Is this normal? Also, I experience a bit of thrashing - which shouldn't occur, as I have 12GiB RAM installed, and a swap partition at 4GiB.

Again, is this normal, and if it isn't, how to fix?
All inputs are appreciated=)

PS: Command TOP, and 1 pressed, returns all four cores.

---

### Post by Vaphell on 2012-07-19
if the program you run is singlethreaded then this is exactly what you see. CPU can't magically break up program code into pieces and give the pieces to different cores to execute everything faster.
Either the program must be multithreaded (its inner architecture enables parallelization which can utilize other cores) or you need to run 4 cpu-heavy singlethreaded programs to tax all cores.

---

### Post by Paqman on 2012-07-19
> **Kols said:**
> 
Is this normal?

Yup. There's still plenty of software that can't take advantage of multiple cores.

The good news is that Linux itself can handle a ludicrous amount of cores, so even if you've got an application that is chewing up a single core, all the other background tasks of the OS will be getting sent to the other cores. So the process will finish a little bit quicker than it would on a single-core machine.

---

### Post by Nixarter on 2012-07-19
Looks like they covered most of it.

There is something called "indexing" that you need to disable that will stop most of the thrashing.  I think there may have been a couple more things to disable, but that was the main one.  I posted a thread here, and nobody had any idea what was going on lol.  Took me forever to figure it out :o  

Now that is my #1 thing to do immediately after installing a new distro.

And as for the page file, certain things are stored there by default, even if there is plenty of RAM free.  I could never figure out how to disable this, unfortunately... though I KNOW it can be done, because some distros have page files disabled by default.  It's my HDD space, and I want it :p

---

### Post by 3Miro on 2012-07-19
Whether an app will use one or more cores depends on the app itself. If the app has been written for single-core, then that's all that it will use. If an app was written to utilize more cores, then the program will spawn several threads and Linux will distribute them among the cores.

Linux powers more than 90% of the world's most powerful computer (check top500.org). Linux is unparalleled when it comes to using your CPU in the most efficient way regardless of how many cores you may have.

---

### Post by MutantJohn on 2012-07-20
Does the number one supercomputer really have ~1.6 million processors in it? And here I was thinking I was spoiling linux by using what Passmark calls a "high-end" processor.

---

### Post by 3Miro on 2012-07-20
> **MutantJohn said:**
> Does the number one supercomputer really have ~1.6 million processors in it? 

Yes, it does.

> 
And here I was thinking I was spoiling linux by using what Passmark calls a "high-end" processor.

They are thinking about high-end desktop computer. You can go to newegg now and buy CPUs with as much as 16 cores, you can easily build a server machine with 32-48 cores and Linux will handle it just fine.

---

### Post by Statia on 2012-07-20
> **Nixarter said:**
> Looks like they covered most of it.

And as for the page file, certain things are stored there by default, even if there is plenty of RAM free.  I could never figure out how to disable this, unfortunately... though I KNOW it can be done, because some distros have page files disabled by default.  It's my HDD space, and I want it :p

**  Swap Space on SSDs **

 One can place a swap partition on an SSD. Note that most modern  desktops with an excess of 2 Gigs of memory rarely use swap at all. The  notable exception is systems which make use of the hibernate feature.  The following is recommended tweak for SSDs using a swap partition that  will reduce the "swappiness" of the system thus avoiding writes to swap: 
 # echo 1 > /proc/sys/vm/swappiness  Or one can simply modify /etc/sysctl.conf as recommended in the [Maximizing Performance]("https://wiki.archlinux.org/index.php/Maximizing_performance#Swappiness") wiki article: 
 vm.swappiness=1 vm.vfs_cache_pressure=50 
Found on [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
when looking for my new system setup.

---

### Post by andrew.46 on 2012-07-20
> **Kols said:**
> I'm wondering how Ubuntu utilizes my CPU. Reason for this is, that whenever I'm running something which requires a bit of calculating power, it seems that core 0 (or the first core, if you prefer it) takes all the load, whereas the other 3 stays pretty much idle (2-8 %).

Try some video encoding with x264, a great example of multiple core use...

---

