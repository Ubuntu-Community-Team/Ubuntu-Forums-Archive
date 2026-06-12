---
title: "Possible Fix to HIGH CPU USAGE in 686 SMP Kernels!"
date: 2006-06-12
forum: General Help
---

### Post by barakaspeed on 2006-06-12
I have been plagued since my install of ubuntu 6.06 with excessively high idle cpu usage running the 686 kernel.  It was the one installed by default during installation for my Pentium M 1.6Ghz.  The culprit usually was Xorg hogging over 35% of cpu power during idle.  You can follow my other thread where I ended up installing the 386 kernel as a work-around: [http://www.ubuntuforums.org/showthread.php?t=192207](http://www.ubuntuforums.org/showthread.php?t=192207)

A MUCH better work-around was offered by sohail (All credit for this goes to him) in this Bug Report I was following: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30570](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30570)

This is what he wrote from there: 
> Guys, have you tried adding this to /etc/rc.local:

echo 1 > /sys/module/processor/parameters/max_cstate

This is what you should do if you want to use a 686 kernel.

Of course, I wish someone would revert the ubuntu patch that *caused*
this in the first place...

Now I'd be the first to admit I'm no Linux Guru.  My educated guess the problem  is solely in SMP support in the 686 kernel being enabled for processors that have no need for it. (aka my Pentium M)

Anyways, I'm glad I can run the 686 kernel on my laptop with less cpu usage and cooler (The fans were kicking on all the time before this)

Thanks to the great community

---

### Post by Patrick-Ruff on 2006-06-12
good job, nice find/research.

---

### Post by no1wantdthisname on 2006-06-12
Wow, thanks.  I've been trying to figure out why cpu load was so high since the beginning of dapper development when SMP support was included by default in the 686 kernel.

---

### Post by jerinjoy on 2006-06-14
I installed the i386 version of dapper drake on my Pentium M 1.6Ghz machine. Should I upgrade to the i686 kernel version? Any advantage in doing so?

---

### Post by GadgetsGuy on 2006-06-14
how do we add this extra line 

what would be the command, as I am still not up to speed with permissions

thanx
GG

---

### Post by barakaspeed on 2006-06-14
jerinjoy, to be completely honest, I have not seen any advantages yet.  I play games, videos, and such on my machine and haven't noticed much of a difference between 386 and 686.  Though having the 686 modded to work properly gives me that piece of mind that my laptop is running at it's most optimal configuration.  I'm probably just crazy for thinking that way..

GadgetsGuy:

```
sudo gedit /etc/rc.local
```

and insert this line into that file.  I placed it the line above exit 0.

```
echo 1 > /sys/module/processor/parameters/max_cstate
```

Here's my modified rc.local file now:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 1 > /sys/module/processor/parameters/max_cstate
exit 0

```

---

### Post by GadgetsGuy on 2006-06-14
OK ... I have done this, and rebooted, yet my hard drive is still spinning non-stop

any other ideas?

I am getting very frustrated by this, and Ubuntu 6.06 (686) was working like a charm until 2 days ago, and quite frankly, if I can not figure this out soon, I will have to go back to Win2000 Pro while I still have a hard drive !!! :(

---

### Post by barakaspeed on 2006-06-14
have you tried the 386 kernel to see if that helps/changes anything?

---

### Post by t0mc4t on 2006-06-15
Sorry if little bit out of topic. But how do we change the kernel that we used? I mean from 386 to 686 or 686 to 386. And how do we check the kernel that we are currently used?
Thanks...

---

### Post by veratyr on 2006-06-15
I'm using XGL with a 686 kernel (has smp support built in now?) and I havn't had any problems with high cpu usage? Granted my P4 is reasonably fast at 3.0GHz.

As for installing a 686 kernel. Open up synaptic and search for "linux-image" and you should find what you are looking for. You may need to install the restricted modules for 3d driver support for whatever kernel you choose to install. Search for "linux-restricted" and install the corresponding modules. Grub usually displays what kernel you are booting to.

*shrug*

---

### Post by nix4me on 2006-06-15
The new kernel sux.  Both the 386 and 686 kernels are sucking up 15% on my boxes.  2 different machines, same thing.

nix4me

---

### Post by xXx 0wn3d xXx on 2006-06-15
This worked great. I was using 33 % of my CPU while doing nothing before but now I'm down to 5 %.

---

### Post by barakaspeed on 2006-06-15
t0mc4t, from the command line type this for your current kernel:

```
uname -a
```

To install other kernels you can use synaptics as stated above or again from the command line type:

```
sudo apt-get install linux-386
```

Change the 386 to 686 if you want that instead.

---

### Post by josh2112 on 2006-06-24
Thanks for the fix!

Another symptom of this problem (for those who aren't watching their CPU usage) is as follows:  Under Kubuntu, the little tooltips that "wipe" across the screen when you hover the mouse cursor over an icon on the kicker were unbearably slow after installing the 686 kernel.

If the single- and multi-processor kernels have been merged for 686, why are there still two packages named "linux-686" and "linux-686-smp"?

And two questions I think have already been echoed in this thread:

1) For a Pentium M, am I gaining any performance by using the 686 kernel with max_cstate = 1, rather than the 386 kernel?

2) What is this max_cstate anyway?  I've already had to knock it down to 2 to get rid of an annoying buzz on my Latitude D510 laptop.  Now it's at 1 to fix this problem.  What does this mean in terms of performance and power usage?

---

### Post by hod139 on 2006-06-25
[quote=josh2112]
And two questions I think have already been echoed in this thread:

1) For a Pentium M, am I gaining any performance by using the 686 kernel with max_cstate = 1, rather than the 386 kernel?

2) What is this max_cstate anyway?  I've already had to knock it down to 2 to get rid of an annoying buzz on my Latitude D510 laptop.  Now it's at 1 to fix this problem.  What does this mean in terms of performance and power usage?[/quote]

I am also interested in hearing feedback about these two questions.  In addition, when the Ubuntu devs finally release an official fix, will our altering of *max_cstate* cause even more issues?

---

### Post by jerinjoy on 2006-08-11
I see from this page:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557)

that this bug has been fixed. So if I upgrade and remove the echo 1>.... line from my /etc/rc.local will it work ok? This affects only the 686 version of Dapper.

Bug Summary: The CPU switches cstates, operating a different frequencies and power consumption based on load. There is a counter that increments when the CPU is idle - after a certain value is reached this changes to a lower power state. cstates 3/4? caused the idle counter to increment at a slower rate so the CPU looked more loaded than it actually was.
I had a performance degradation on my Pentium M machine. On the Dual Core SMP machines it works fine.

Correct me if I'm wrong.

---

