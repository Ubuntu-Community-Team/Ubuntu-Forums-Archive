---
title: "CPU frequency scaling with multiple cores and a single bound thread?"
date: 2010-11-13
forum: General Help
---

### Post by czr114 on 2010-11-13
System: Ubuntu 10.04 x64, fully updated, multiple cores

I just noticed a potential problem with how CPU frequency scaling is implemented in Ubuntu, from the user's perspective.

Being unfamiliar with where exactly the problem lies, I may need some help finding the right upstream to report this. I'm not sure whether this is an Ubuntu issue, an applet issue, or a kernel issue.

I use the CPU Frequency Scaling Monitor (2.30.0) applet on my panel to monitor and adjust frequency scaling as needed.

Using the "Ondemand" setting helps balance power consumption with performance across a wide variety of situations by reducing the CPU clock when the processor is under light load. Energy efficiency is something good not only for laptops, but also for desktops. Secondly, keeping operating temperatures down both extends the life of the equipment, as well as reduces energy used for dwelling or office cooling.

For most situations, ondemand is fine, although it appears to be hitting some limits with regard to multiple core systems performing certain specific tasks.

I have noticed that, when a single thread is CPU bound on a multicore system, Ubuntu's frequency scaling does not scale up to deliver additional frequency to the bound thread which is operating at 100% of core, due to unutilized CPU time on the remaining cores.

Despite the purpose of the ondemand setting being to bring additional performance online as necessary, something in the internals somewhere seems to interpret less than maximum utilization across all cores as an underutilized condition, even if a single thread has become CPU bound.

For some reason, the internals monitoring and adjusting CPU frequency are falsely interpreting the aggregate core underutilization as a sign the system cannot benefit from a higher frequency, and thus downscale the processor accordingly.

This binds up CPU intensive tasks until the user manually adjusts the CPU's frequency to its performance setting, for those tasks he knows to be CPU bound but the system fails to interpret as such.

This is a huge problem for single-threaded applications, particularly something like HD video playback which needs to be done in real time.

The laptop system I discovered this on will only smoothly decode 1080p if the system is manually set to maximum frequency. Otherwise, both VLC and Totem become CPU bound on a single thread, the system doesn't increase the frequency, and playback becomes choppy as a result.

I have also confirmed this on large file hashing operations, and through a quick while(1){} implementation I put together to stress the CPU. One instance of while(1) chokes on a sub-maximum frequency, whereas n instances of while(1) [where n=# of cores] results in proper scaling to maximum.

This is not a huge problem for those who monitor their CPU's frequency and understand when additional performance is required.

This is a huge problem for less savvy users, as they not only do not understand problems like these, but also, that the monitor applet is not a default inclusion of Ubuntu's GNOME panel.

I'm not sure what performance profile Ubuntu defaults to out of the box.

If it defaults to the ondemand setting described above, unaware users will be needlessly CPU bound, and may falsely assume that their poor realtime performance is an inherent OS problem.

While this problem is easy to pawn off on a application programming issue, not an OS issue, consider that not all tasks can be parallelized, and that legacy code will take years to bring forward into a multi-core world.

---

### Post by efflandt on 2010-11-13
You don't say what cpu you have.  But I wonder if trying to constantly monitor and control it might actually interrupt it or interfere with what it should do automatically.

I have an i5 650 3.2 GHz which I believe is 2 cores with hyperthreading.  It does not seem to do turbo yet, but the 4 virtual cores automatically operate independently at whatever speed is required.

This is 64-bit Maverick idling:
```
grep MHz /proc/cpuinfo
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
```This is glxgears running my GT 220 gpu 100% without vsync
```
grep MHz /proc/cpuinfo
cpu MHz        : 1200.000
cpu MHz        : 3201.000
cpu MHz        : 1200.000
cpu MHz        : 3201.000
grep MHz /proc/cpuinfo
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 3201.000
cpu MHz        : 3201.000
```Do your cores always run at the same speed as each other, instead of independently on demand.

The only 1080 video I have is a Quantum of Solace preview which is very fast paced, but smooth.  But it is flash and the video itself is only 25 frames per second.  So that is not very demanding of cpu time.

---

### Post by mc4man on 2010-11-13
I would think (not sure), that the actual CPU scaling algorithms are part of the kernel.

( For myself (intel core2duo), I found ondemand not performing properly, many videos weren't playing back smoothly  due to not scaling up when it was clearly needed.
All of that and some better performance overall while using ondemand  was achieved by lowering the up_theshold which, atm in ubuntu, defaults to a value of 95.
i used the ondemand script to lower it between 65 and 75 - atm it's 65 on this machine

---

### Post by dcstar on 2010-11-14
> **czr114 said:**
> 
..........
I just noticed a potential problem with how CPU frequency scaling is implemented in Ubuntu, from the user's perspective.

Being unfamiliar with where exactly the problem lies, I may need some help finding the right upstream to report this. I'm not sure whether this is an Ubuntu issue, an applet issue, or a kernel issue.

I use the CPU Frequency Scaling Monitor (2.30.0) applet on my panel to monitor and adjust frequency scaling as needed.
...........
The laptop system I discovered this on will only smoothly decode 1080p if the system is manually set to maximum frequency. Otherwise, both VLC and Totem become CPU bound on a single thread, the system doesn't increase the frequency, and playback becomes choppy as a result.
..........
I'm not sure what performance profile Ubuntu defaults to out of the box.

If it defaults to the ondemand setting described above, unaware users will be needlessly CPU bound, and may falsely assume that their poor realtime performance is an inherent OS problem.
..........

Your whole "issue" seems based on a false premise. The CPU monitoring applet monitors only **individual** cores, you need a separate applet for **each** core in your system specifically set to monitor that particular core.

If one core is already at 100% running a single core thread, then the other cores are irrelevant to the performance of **that** thread. There may well be issues where the other cores running at lower clock rates are utilised by other processes and the various internal CPU core sharing mechanisms have to adjust to the differing rates, but 100% is 100% and the whole issue of single threaded processes is that they cannot be split and shared between available resources.

You can install the **powernowd** package and see if that manages things differently than the default CPU management.

When Ubuntu boots the default kernel setting is "Performance", the **/etc/rc2.d/S99ondemand** script changes it to "Ondemand" after 60 seconds.

---

