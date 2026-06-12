---
title: "Help resolve Kernel Panic please"
date: 2011-11-25
forum: General Help
---

### Post by SuperFreak on 2011-11-25
I booted my computer this morning and it went into Kernel Panic. I really do not understand how to deal with this and what I did was a hard restart which worked. After reading that Panic Attack is analogous to Blue Screen of Death in Windows I am concerned. It there anything I should do about this? The error message on boot up is more or less as below

Thanks


udevd-work[358]: open /dev/null failed: no such file or directory
run-init: nuking initramfs contents: Directory not empty
udevd-work[116]: inotify_add_watch(6, /dev/sdb, 10) failed: No such file or directory[ 2.068478] Kernel panic - not syncing: Attempted to kill init!

---

### Post by dabl on 2011-11-25
Google "udevd-work dev null failed" and you will find lots of information.

---

### Post by SuperFreak on 2011-11-25
There seems to be a bug report in Launchpad of "udevd-work dev null failed" which has not yet been resolved although the bug goes back a few years. I have been having the "udevd-work dev null failed" message on start up virtually since I installed 10.10 back in 2010 and I haven't been overly concerned about it. 
What I am concerned about is the Kernel Panic message which came after  "udevd-work dev null failed" . Is that an indication of hardware failure?

---

### Post by dabl on 2011-11-25
Kernel panic is never a good thing.  If it only happens one time, it may be some kind of anomaly.  If you can find a pattern of kernel panics, then maybe Google can turn something up.  But usually it means there is some fundamental incompatibility between the running kernel and your hardware.  If it "always used to work" on your hardware, and all of sudden you start getting kernel panics, it is time to start testing memory and hard drive, and then the other bits of hardware that you have.

---

### Post by SuperFreak on 2011-11-25
Thanks,

I did replace bad memory about 1 month ago. I will have a look at the SMART attributes of my HDs


ed: SMART attributes check out as good

---

### Post by dabl on 2011-11-25
I assume you carefully matched the speed of the replacement memory module(s) to what your motherboard is specified to use.

If so, the next time you are leaving your computer for some hours (like overnight), I would boot the live CD and start memtest86, and let it run all night.

Also, do you have thermal monitoring available -- is there any chance of an overheating issue?  Does the CPU have a heatsink -- any chance that it is clogged with dust, or the CPU fan has failed, or one leg of the heatsink has come loose, or anything like that?

---

### Post by SuperFreak on 2011-11-25
Bought Corsair memory and as I recall I used the memory selection tool on that web site to select it(I will recheck). Also I ran Mem86 on that memory when I installed it and it had no errors.
I had cleaned the inside of my case with a can of aerosol recently(last few weeks)
I do run temperature checks and everything is usually OK except the video card which is usually about 49 C which shows as red on the temp monitor. However this occurred when starting up so the video card would not be hot then

---

### Post by dabl on 2011-11-25
I would still run the memtest86 again, for at least 4 hours.

One thing you could try, to troubleshoot between hardware and OS, you could try booting a Live CD of some other Linux distribution.  For example, [[COLOR="SeaGreen"]**aptosid**[/COLOR]](http://aptosid.com/index.php?module=news&func=display&sid=28) is pretty good on detecting hardware.  If the aptosid Live CD will for hours with no kernel panic, you can be suspicious of Ubuntu.  If aptosid also kernel panics, then you must suspect the hardware

---

### Post by SuperFreak on 2011-11-25
Thank you for your help. I have rebooted a few times without Kernel Panic. I will try your suggestions, perhaps I will run Mem86 tonight.

---

### Post by SuperFreak on 2011-12-06
I ran Memtest86 for over 4 hours (see image) with no errors. I don't think the memory is the problem. Since my last post after over dozen reboots without issue I had another instance of Kernel Panic. I really don't know how to diagnose the issue can anybody tell me anything based on the output I put in the first post? The latest Kernel Panic was similar but had more lines of output but I am afraid I didn't record it; I just rebooted.

---

