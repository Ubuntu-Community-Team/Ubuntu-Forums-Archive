---
title: "Linux Kernel 3.0 Battery Life/Power Consumption"
date: 2011-08-10
forum: General Help
---

### Post by steevven1 on 2011-08-10
Hello all,

I have just upgraded from Linux kernel 2.6.38 to Linux 3.0 by installing the .deb packages from Oneiric, and I am experiencing a major drop in battery life (about 25% less time) on my laptop. It is also running noticeably hotter. Reverting to the older kernel brings back the good battery life and cool temperatures.

I need the 3.0 kernel because of some of the drivers it contains. Does anyone have any idea what to do to fix this power issue? Is the 3.0 kernel just supposed to be that much worse?

I'm running Xubuntu 11.04 64-bit.

Thank you!

---

### Post by wastedtime-fr on 2011-08-10
> **steevven1 said:**
> Hello all,

I have just upgraded from Linux kernel 2.6.38 to Linux 3.0 by installing the .deb packages from Oneiric, and I am experiencing a major drop in battery life (about 25% less time) on my laptop. It is also running noticeably hotter. Reverting to the older kernel brings back the good battery life and cool temperatures.

I need the 3.0 kernel because of some of the drivers it contains. Does anyone have any idea what to do to fix this power issue? Is the 3.0 kernel just supposed to be that much worse?

I'm running Xubuntu 11.04 64-bit.

Thank you!

Not running ubuntu here but gentoo, and I noticed exactly the opposite... Some 20 to 40% more battery life.
Do you have everything else the same, for instance, free drivers vs ATI/NVidia ones ?
What is the driver you need? If it is wifi and it is working, it may consume more power...
If everything else fails and you know how to read a kernel .config file, they may be available in /proc/config.gz 
My first guess (captain obvious here :D) would be to mess in power management stuff, but it can also be scheduler related...

Hope this helps.

---

### Post by steevven1 on 2011-08-10
Also: Has anyone else installed Linux 3.0 and monitored their power consumption?

Did you experience higher power consumption? The same? Lower?

---

### Post by steevven1 on 2011-08-10
> **wastedtime-fr said:**
> Not running ubuntu here but gentoo, and I noticed exactly the opposite... Some 20 to 40% more battery life.
Do you have everything else the same, for instance, free drivers vs ATI/NVidia ones ?
What is the driver you need? If it is wifi and it is working, it may consume more power...
If everything else fails and you know how to read a kernel .config file, they may be available in /proc/config.gz 
My first guess (captain obvious here :D) would be to mess in power management stuff, but it can also be scheduler related...

Hope this helps.


Thanks for the suggestions. Maybe you can point me in the right direction a little more. It is not wifi, but graphics. I was experiencing graphics glitches with the previous kernel with my Intel Sandy Bridge processor, and the new kernel has cleared them up.

As far as I know, I have changed NOTHING but the kernel.

Ther weird thing is: The computer is running hotter, but "top" shows 0% processor usage...

---

### Post by wastedtime-fr on 2011-08-10
> **steevven1 said:**
> 
As far as I know, I have changed NOTHING but the kernel.

Ther weird thing is: The computer is running hotter, but "top" shows 0% processor usage...

can you install powertop? 
Very usefull to debug what is consuming your precious milliwatts.
It will also tell you if your processor doesn't slow down as it should.
Exemple:

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 0.0%)
polling           0.0ms ( 0.0%)
C1                1.0ms (11.0%)
C2                7.2ms (97.0%)


Wakeups-from-idle per second : 245.7    interval: 5.0s
Power usage (ACPI estimate): 7.2W (7.8 hours)



Also, what is your default governor for cpu frequency? On laptop battery, you should be going with ondemand or conservative.

---

### Post by steevven1 on 2011-08-10
> **wastedtime-fr said:**
> can you install powertop? 
Very usefull to debug what is consuming your precious milliwatts.
It will also tell you if your processor doesn't slow down as it should.
Exemple:

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 0.0%)
polling           0.0ms ( 0.0%)
C1                1.0ms (11.0%)
C2                7.2ms (97.0%)


Wakeups-from-idle per second : 245.7    interval: 5.0s
Power usage (ACPI estimate): 7.2W (7.8 hours)



Also, what is your default governor for cpu frequency? On laptop battery, you should be going with ondemand or conservative.


Installing powertop right now. What should I do with it once installed?

And as far as your other question...What do I do to find that information out?

Also, if my CPU is reading 0% in top, wouldn't it probably be something else causing the power issues, or no?

---

### Post by steevven1 on 2011-08-10
sudo powertop yields the following interesting information:

Top causes for wakeups:
  52.9% (317.8)   [Rescheduling interrupts] <kernel IPI>

What is that?

Also, it is giving me three "suggestions," which include USB autosuspend for non-input devices, increase the VM dirty writeback time from 5.00 to 15 seconds, and enable device power management. Should I do these?

---

### Post by wastedtime-fr on 2011-08-10
> **steevven1 said:**
> Installing powertop right now. What should I do with it once installed?

And as far as your other question...What do I do to find that information out?

Also, if my CPU is reading 0% in top, wouldn't it probably be something else causing the power issues, or no?

just run powertop on a terminal

next, also on a terminal, what does 
lsmod | grep cpufreq
returns?

And to answer your last question, top gives the cpu workload. The frequency will be throttled down only if the power management, ie cpufreq governor, asks for it.

---

### Post by steevven1 on 2011-08-10
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 5.9%)       Turbo Mode     6.6%
polling           0.1ms ( 0.0%)         1.80 Ghz     0.3%
C1 mwait          0.5ms ( 2.2%)         1.60 Ghz     0.5%
C2 mwait          0.9ms ( 1.3%)         1200 Mhz     0.5%
C3 mwait          0.9ms ( 0.1%)          800 Mhz    92.0%
C4 mwait          4.8ms (90.5%)

---

### Post by steevven1 on 2011-08-10
lsmod | grep cpufreq yields no output at all.

---

### Post by wastedtime-fr on 2011-08-10
> **steevven1 said:**
> sudo powertop yields the following interesting information:

Top causes for wakeups:
  52.9% (317.8)   [Rescheduling interrupts] <kernel IPI>

What is that?

Also, it is giving me three "suggestions," which include USB autosuspend for non-input devices, increase the VM dirty writeback time from 5.00 to 15 seconds, and enable device power management. Should I do these?

The suggestions are quite correct usually. And they are for your current session only, so even if you disable something usefull, it will be there at the nexte reboot.
Powertop is a debuging tools for power management. If you want the tweaks to be final, you need to modify some config files (I don't know how they are generated/modified with ubuntu since i'm a hardcore gentoo/command line fan:D).

The interupts rescheduling is clearly kernel related, but since i don't know what is the .config file used to compile it, I can't say what to do with it. 
It seems that there is a ubuntu wiki about this...
[https://help.ubuntu.com/community/ReschedulingInterrupts](https://help.ubuntu.com/community/ReschedulingInterrupts)

---

### Post by steevven1 on 2011-08-10
How do I boot with a certain kernel parameter, as the page suggests? Also, are these changes permanent? How would I make them permanent if I wanted to?

---

### Post by sbraz on 2011-08-10
this might be an old kernel bug, try adding this option to the kernel boot parameters.

```
pcie_aspm=force
```

---

### Post by steevven1 on 2011-08-10
> **sbraz said:**
> this might be an old kernel bug, try adding this option to the kernel boot parameters.

```
pcie_aspm=force
```

Thanks, but how do I edit kernel parameters?

---

### Post by wastedtime-fr on 2011-08-10
> **steevven1 said:**
> How do I boot with a certain kernel parameter, as the page suggests? Also, are these changes permanent? How would I make them permanent if I wanted to?

This is done in the bootloader config file. You should install graphical tools like startupmanager to mess with them.

---

### Post by steevven1 on 2011-08-10
When you select the kernel with GRUB and press "e" and add in a line of text and then press ctrl+x to continue booting, is that changing a kernel parameter? I tried that iwth "pcie_aspm=force" and it did not solve the issue.

---

### Post by steevven1 on 2011-08-10
Update: **"[Rescheduling interrupts] <kernel IPI>" is definitely the problem.** Booting to the old kernel and running powertop showed no trace of this source of wakeups.

I'm trying to try the suggestions in the Ubuntu wiki link, but I'm not even 100% sure if what I'm doing is the right thing: Is pressing "e" on the 3.0 kernel and typing the options the right thing to do?

---

### Post by wastedtime-fr on 2011-08-10
> **steevven1 said:**
> Update: **"[Rescheduling interrupts] <kernel IPI>" is definitely the problem.** Booting to the old kernel and running powertop showed no trace of this source of wakeups.

I'm trying to try the suggestions in the Ubuntu wiki link, but I'm not even 100% sure if what I'm doing is the right thing: Is pressing "e" on the 3.0 kernel and typing the options the right thing to do?

It seems correct to me for testing purpose.

---

### Post by steevven1 on 2011-08-10
I tried all of the following kernel parameters (result in italics):

pcie_aspm=force
*No improvement*

acpi=noirq
*No improvement*

noapic
*Command not recognized. Won't boot.*

nolapic
*Command not recognized. Won't boot.*

acpi=off
*No improvement*

More ideas?

---

### Post by steevven1 on 2011-08-11
Any more ideas? I haven't given up hope, but I have nothing else to try at all.

I have to be able to use the 3.0 kernel, but I can't live with this insane hit in battery life. There's got to be a fix, or else everyone would be complaining about kernel 3.0.

---

### Post by sbraz on 2011-08-11
> **steevven1 said:**
> Thanks, but how do I edit kernel parameters?

> **steevven1 said:**
> **When you select the kernel with GRUB and press "e" and add in a line of text and then press ctrl+x to continue booting, is that changing a kernel parameter? I tried that iwth "pcie_aspm=force" and it did not solve the issue.**

> **steevven1 said:**
> Update: **"[Rescheduling interrupts] <kernel IPI>" is definitely the problem.** Booting to the old kernel and running powertop showed no trace of this source of wakeups.

I'm trying to try the suggestions in the Ubuntu wiki link, but I'm not even 100% sure if what I'm doing is the right thing: Is pressing "e" on the 3.0 kernel and typing the options the right thing to do?


here's how: [http://imageshack.us/photo/my-images/215/201108110707057.jpg/](http://imageshack.us/photo/my-images/215/201108110707057.jpg/)

that high rescheduling reported by powertop might indicate a kernel bug. since you are using an ubuntu official kernel, if nobody around here finds a solution, you should consider filing a bug. [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)


now, why did you install a new kernel? :)

---

### Post by steevven1 on 2011-08-11
Thanks for the info, sbraz, but I already figured that out and posted the results in post #19. They weren't very encouraging :-/

I installed the new kernel because it contains a fix for graphics glitches I was having with my Sandy Bridge processor (and it has lived up to that...no glitches since installing!), but I can't live with this hot laptop and short battery life, I'm afraid :-/

---

### Post by sbraz on 2011-08-11
check this out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

try adding this parameter now **i915.i915_enable_rc6=1**


also, this might help: [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=sandy+bridge](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=sandy+bridge)

---

### Post by steevven1 on 2011-08-11
> **sbraz said:**
> check this out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

try adding this parameter now **i915.i915_enable_rc6=1**


also, this might help: [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=sandy+bridge](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=sandy+bridge)

Thanks for the suggestion. That looked EXTREMELY promising, but alas, it did nothing :-(

I checked out the second link, but see nothing more of relevance there.

Thanks again for the comment.

---

### Post by wastedtime-fr on 2011-08-11
> **sbraz said:**
> here's how: [http://imageshack.us/photo/my-images/215/201108110707057.jpg/](http://imageshack.us/photo/my-images/215/201108110707057.jpg/)

that high rescheduling reported by powertop might indicate a kernel bug. since you are using an ubuntu official kernel, if nobody around here finds a solution, you should consider filing a bug. [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)


Since 3.0.1 is out from kernel.org as stable, you may also give it a try when it is packaged for ubuntu. Your problem may be already solved...

---

### Post by CaptainMark on 2011-08-11
ive noticed the same issues running oneric, i used to run at about 45º for cpu temp in natty and now im running at about 50º in oneiric and my fan has increased from about 3000rpm to 3500 rpm

---

### Post by steevven1 on 2011-08-11
> **wastedtime-fr said:**
> Since 3.0.1 is out from kernel.org as stable, you may also give it a try when it is packaged for ubuntu. Your problem may be already solved...

I've already installed 3.0.1-030001-generic

Problem still there :-(

---

### Post by sbraz on 2011-08-11
> **wastedtime-fr said:**
> Since 3.0.1 is out from kernel.org as stable, you may also give it a try when it is packaged for ubuntu. Your problem may be already solved...
it is possible.

i'm out of ideas atm, unless someone is in the mood for building a vanilla kernel to test 3.0.1 or even 3.1-rc1.

---

### Post by steevven1 on 2011-08-11
> **CaptainMark said:**
> ive noticed the same issues running oneric, i used to run at about 45º for cpu temp in natty and now im running at about 50º in oneiric and my fan has increased from about 3000rpm to 3500 rpm

CaptainMark, what is the output of:

```
cat /proc/cpuinfo | grep name | head -1
```

On your system?

---

### Post by steevven1 on 2011-08-11
> **sbraz said:**
> it is possible.

i'm out of ideas atm, unless someone is in the mood for building a vanilla kernel to test 3.0.1 or even 3.1-rc1.


I'm personally up for anything...I just want this problem solved. With that said, I don't know the meaning of what you just said :-/

I have already installed 3.0.1, but I have not tried 3.1rc1 because there is no ubuntu .deb package for it...

---

### Post by wastedtime-fr on 2011-08-11
> **steevven1 said:**
> I'm personally up for anything...I just want this problem solved. With that said, I don't know the meaning of what you just said :-/

I have already installed 3.0.1, but I have not tried 3.1rc1 because there is no ubuntu .deb package for it...

Basically, he said to go to kernel.org, get the sources, and build your own kernel to test if it is kernel related, or ubuntu kernel patch/config related.

Can you provide me your kernel config for 3.0.0 ? It should be available at /proc/config.gz 
I will try to build a vanilla kernel (well, gentoo but it is almost the same) with ubuntu settings, and if i encouter your problem, then you will really have to fill a bug with the kernel compilers at ubuntu ;)

---

### Post by sbraz on 2011-08-11
> **steevven1 said:**
> I'm personally up for anything...I just want this problem solved. With that said, I don't know the meaning of what you just said :-/

I have already installed 3.0.1, but I have not tried 3.1rc1 because there is no ubuntu .deb package for it...
hmm, let me explain:
many if not all linux distros provides precompiled kernel packages to save the user from the somewhat tedious work that is compiling a kernel manually. this is a great *feature* we're looking at.
anyway for me that wasn't enough as i had problems with a bunch of things with my netbook and apparently the only solution were to compile a new kernel as there wasn't any update in the repos... so i started learning the aforementioned tedious procedure.
there are a lot of things that you need to know to make it happen, so please forgive me but i'm not going to explain to you here. :)

let me clarify something before someone slaps me: i'm NOT trying to discourage you from learning about it, it's just that there are tons of guides around the net about compiling a kernel from sources.


my advice is this: provided that i don't know what kind video glitches you are trying to fix, you can boot the old kernel when you have to use your laptop on battery and vice-versa, just until a new .deb kernel solves both of your issues. ;)

> **wastedtime-fr said:**
> Basically, he said to go to kernel.org, get the sources, and build your own kernel to test if it is kernel related, or ubuntu kernel patch/config related.

Can you provide me your kernel config for 3.0.0 ? It should be available at /proc/config.gz 
I will try to build a vanilla kernel (well, gentoo but it is almost the same) with ubuntu settings, and if i encouter your problem, then you will really have to fill a bug with the kernel compilers at ubuntu ;)
exactly.
you shouldn't need ubuntu .config file imho but it's worth testing. :)

i have a question though: do you run gentoo on the same platform as steevven1?

---

### Post by el_koraco on 2011-08-11
This is for 38 and 39, but it's working for me with 36, so it might help you too.

[http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972)

---

### Post by wastedtime-fr on 2011-08-11
> **sbraz said:**
> hmm, let me explain:
my advice is this: provided that i don't know what kind video glitches you are trying to fix, you can boot the old kernel when you have to use your laptop on battery and vice-versa, just until a new .deb kernel solves both of your issues. ;)

exactly.
you shouldn't need ubuntu .config file imho but it's worth testing. :)

i have a question though: do you run gentoo on the same platform as steevven1?

Not the same hardware. AMD E350 Zacate here (hp dm1z 3130) and kernel 3 gave me 25% IMPROVEMENT :D that's why I stepped in when someone try to imply that 3.0.0 is a bad kernel, this even if I'm not a ubuntu fan.

I wanted the config file to see if the problem starts when using this (I have been using a 3 kernel for almost a month, and it is just great!). There are new stuff in the .config about irq attribution/ io schedulling (at least that's what i recall from my fast trip in the wonderful work of menuconfig, and I didn't mess with it, but some guys at ubuntu may have ;) )
My .config is almost the same that the one I used for 2.6.39 (i used make oldconfig to reuse it).

---

### Post by LowSky on 2011-08-11
I'm using the 3.0 Kernel with a Intel N270 and it runs great. Battery life seems to be about 5-7, or 12-15 hours using sleep mode here and there on a 9 cell battery.

---

### Post by steevven1 on 2011-08-11
> **el_koraco said:**
> This is for 38 and 39, but it's working for me with 36, so it might help you too.

[http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972)


Thank you for the suggestion. We discussed this fix earlier in the thread, and unfortunately, it does not work for me :-(

---

### Post by steevven1 on 2011-08-11
> **wastedtime-fr said:**
> Basically, he said to go to kernel.org, get the sources, and build your own kernel to test if it is kernel related, or ubuntu kernel patch/config related.

Can you provide me your kernel config for 3.0.0 ? It should be available at /proc/config.gz 
I will try to build a vanilla kernel (well, gentoo but it is almost the same) with ubuntu settings, and if i encouter your problem, then you will really have to fill a bug with the kernel compilers at ubuntu ;)


Is this a reasonable guide for compiling a kernel? I would be willing to give it a try with 3.1rc1 if this looks like a good guide. If it is missing any steps or suggestions, PLEASE chime in before I begin :-) - [http://www.techytalk.info/compile-upstream-kernel-org-ubuntu-debian/](http://www.techytalk.info/compile-upstream-kernel-org-ubuntu-debian/)

About the kernel config...That file (/proc/config.gz) does not exist for me :-/

---

### Post by sbraz on 2011-08-11
> **wastedtime-fr said:**
> Not the same hardware. AMD E350 Zacate here (hp dm1z 3130) and **kernel 3 gave me 25% IMPROVEMENT** :D that's why I stepped in when someone try to imply that 3.0.0 is a bad kernel, this even if I'm not a ubuntu fan.

I wanted the config file to see if the problem starts when using this (I have been using a 3 kernel for almost a month, and it is just great!). There are new stuff in the .config about irq attribution/ io schedulling (at least that's what i recall from my fast trip in the wonderful work of menuconfig, and I didn't mess with it, but some guys at ubuntu may have ;) )
My .config is almost the same that the one I used for 2.6.39 (i used make oldconfig to reuse it).
awesome! can you too post your .config file? the purpouse is to diff them. :)

> **steevven1 said:**
> About the kernel config...That file (/proc/config.gz) does not exist for me :-/
the existence of the /proc/config.gz file depends on the kernel configuration. i normally disable this (i'm not sure it's a nice idea in every distro btw ) as you can find your config files in /boot/config*
here's an example:
```
root@sbraz-netbook:/# cd /boot/
root@sbraz-netbook:/boot# ll
total 29638
drwxr-xr-x  3 root root     520 2011-08-12 03:10 ./
drwxr-xr-x 25 root root     664 2011-08-05 00:30 ../
-rw-r--r--  1 root root  700977 2011-07-12 02:52 abi-2.6.35-30-generic
-rw-r--r--  1 root root  122657 2011-07-12 02:52 **config-2.6.35-30-generic**
-rw-r--r--  1 root root   90449 2011-08-12 01:16 **config-2.6.39.3-custom**
drwxr-xr-x  3 root root    5776 2011-08-12 01:17 grub/
-rw-r--r--  1 root root 8733913 2011-08-04 18:25 initrd.img-2.6.35-30-generic
-rw-r--r--  1 root root 7774752 2011-08-12 01:49 initrd.img-2.6.39.3-custom
-rw-r--r--  1 root root 2345040 2011-07-12 02:52 System.map-2.6.35-30-generic
-rw-r--r--  1 root root 2167814 2011-08-12 01:16 System.map-2.6.39.3-custom
-rw-r--r--  1 root root    1336 2011-07-12 02:59 vmcoreinfo-2.6.35-30-generic
-rw-r--r--  1 root root 4348176 2011-07-12 02:52 vmlinuz-2.6.35-30-generic
-rw-r--r--  1 root root 4004448 2011-08-12 01:16 vmlinuz-2.6.39.3-custom
```
so you can do something like this, and attach the file in a message here:
```
sbraz@sbraz-netbook:~$ cat /boot/config-2.6.39.3-custom > /home/sbraz/Desktop/config
```

---

### Post by pqwoerituytrueiwoq on 2011-08-11
> **sbraz said:**
> so you can do something like this, and attach the file in a message here:
```
sbraz@sbraz-netbook:~$ cat /boot/config-2.6.39.3-custom > /home/sbraz/Desktop/config
```
why not just copy it? it would be more efficient
```
cp /boot/config-2.6.39.3-custom /home/sbraz/Desktop/config
```

---

### Post by steevven1 on 2011-08-11
Okay, I've attached all three of my kernel configs. The 3-series kernels have the power consumption problem and no graphics problem; the 2-series kernel has no power issues, but graphics glitches.

Again, my processor is a Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz (Sandy Bridge).

Not sure what you're after here, but thanks a lot for the help!!!

Also, did anyone look at that kernel compiling guide I linked to? Worth me trying it for kernel 3.1rc1? Any tips?

Thank you all so much for continuing to reply.

Let's get this bug solved! :-)

---

### Post by sbraz on 2011-08-12
> **pqwoerituytrueiwoq said:**
> why not just copy it? it would be more efficient
```
cp /boot/config-2.6.39.3-custom /home/sbraz/Desktop/config
```
:D even if both commands yields the same result you are totally right. i was cat'ing stuff somewhere and i ended up using cat to copy a file. :redface:

> **steevven1 said:**
> Okay, I've attached all three of my kernel configs. The 3-series kernels have the power consumption problem and no graphics problem; the 2-series kernel has no power issues, but graphics glitches.

Again, my processor is a Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz (Sandy Bridge).

Not sure what you're after here, but thanks a lot for the help!!!

**Also, did anyone look at that kernel compiling guide I linked to? Worth me trying it for kernel 3.1rc1? Any tips?**

THANK YOU ALL.

Let's get this bug solved! :-)
that guide makes sense but i prefer "make" instead of "make-kpkg", i don't know why (but it works so... :D).

this is a humble script i use for building:
```
root@sbraz-netbook:/usr/src/linux-2.6.39.3/source# cat ./build 
#
# cleanup
#
make clean
sync
make-kpkg clean
sync
#
# build new kernel
#
date > ../compile-time
make deb-pkg
date >> ../compile-time
sync
rm ../linux-headers*
#
# choose your preferred deus-ex-machina
#
#shutdown -h now
#reboot
```

there are some patches for ubuntu (look at the attachment) to apply to the kernel source as soon as you have untarred the source:
```
root@sbraz-netbook:/usr/src/linux-2.6.39.3/source# cat apply-patches 
#!/bin/sh
# 2.6.39+
patch -p1 < /usr/src/kernel-patches/39/0001-AppArmor-compatibility-patch-for-v5-network-controll.patch
patch -p1 < /usr/src/kernel-patches/39/0002-AppArmor-compatibility-patch-for-v5-interface.patch
patch -p1 < /usr/src/kernel-patches/39/0003-AppArmor-Allow-dfa-backward-compatibility-with-broke.patch
patch -p1 < /usr/src/kernel-patches/ureadahead.patch
```



i'll have a look at those config files you posted but not now... it's 6:28AM here. :)

btw, i hope you manage to solve your problems without compiling a new kernel or you might end up like me:
[[IMG]http://img687.imageshack.us/img687/1066/kernelfrenzylol.th.png[/IMG]](http://imageshack.us/photo/my-images/687/kernelfrenzylol.png/)

:popcorn:

---

### Post by steevven1 on 2011-08-12
Alrighty. Thank you for the info. I'll eventually try compiling the 3.1rc1 kernel, but not now. It's quite late here too :-)

And yes...I hope we can get this solved without compiling a new kernel too. Even if I compile the new kernel, there's no guarantee it will fix the issue.

Any more ideas are welcome in the meantime!

---

### Post by wastedtime-fr on 2011-08-12
I'm currently compiling 3.0.0 with Steevven's .config. 
I'll post more when i'm done

> **sbraz said:**
> awesome! can you too post your .config file? the purpouse is to diff them. :)



Here you are:

---

### Post by wastedtime-fr on 2011-08-12
> **wastedtime-fr said:**
> I'm currently compiling 3.0.0 with Steevven's .config. 
I'll post more when i'm done
Here you are:
<RANT>
This will take some time, I'm amazed at how many unusefull stuff are in there... 
Maybe that's the stock kernel philosophy, but who around here uses gfs??? 
And that is not the most obscure...
</RANT>

---

### Post by sbraz on 2011-08-12
> **wastedtime-fr said:**
> <RANT>
This will take some time, I'm amazed at how many unusefull stuff are in there... 
Maybe that's the stock kernel philosophy, but who around here uses gfs??? 
And that is not the most obscure...
</RANT>
i agree.

steevven1 try booting adding **maxcpus=1** to the kernel options and run powertop again. try **maxcpus=0** too.

---

### Post by wastedtime-fr on 2011-08-12
> **sbraz said:**
> i agree.


3200 modules :shock:
3 hours of compilation for a kernel... When I'm doing mine, if it takes more than 20 mintues, I find it already too long...

By the way, due to me not using initramfs, I had to add the sata controller built in, and also deactivate modsetting for radeon since it crashes on my hardware. Other than that, everything seems to work... slowly and very hot.

Ok, I'm done and it clearly is a mess. 
The problem is reproduced on my machine. The cpu never slows down due to irq rescheduling. 
=> This make the laptop heat like crazy. I would advise not to use this kernel for anyone using a laptop...
I'm going to try to find the correct setting to change in the .config and i'll tell you when i'm done.

---

### Post by wastedtime-fr on 2011-08-12
> **wastedtime-fr said:**
> 3200 modules :shock:
Ok, I'm done and it clearly is a mess. 
The problem is reproduced on my machine. The cpu never slows down due to irq rescheduling. 

I'm going to try to find the correct setting to change in the .config and i'll tell you when i'm done.

Culprit found!
In menuconfig:
General setup -> IRQ subsystem : Sparse irq numbering should be deactivated. 

This brings back normal temperature and battery life... 
Now, either you recompile a kernel changing this, or you talk about this issue to the official maintenairs of this package... 

Now, I'm going back to my small and neat kernel. Good luck with this :D

---

### Post by sbraz on 2011-08-12
> **wastedtime-fr said:**
> Ok, I'm done and it clearly is a mess. 
The problem is reproduced on my machine. The cpu never slows down due to irq rescheduling. 
=> This make the laptop heat like crazy. I would advise not to use this kernel for anyone using a laptop...
I'm going to try to find the correct setting to change in the .config and i'll tell you when i'm done.
hmm can you test the same kernel parameters i proposed earlier to steevven1? does setting **acpi=noirq noapic nolapic acpi=off** make any difference?

also, could you try compiling again (as time permits) disabling "Automatic process group scheduling" (CONFIG_SCHED_AUTOGROUP)? it's under "general setup" in menuconfig?

OT: i don't know if you already know about this: since do you have a dual core cpu you should try passing **make -j2** to compile dual-threaded.

---

### Post by sbraz on 2011-08-12
> **wastedtime-fr said:**
> Culprit found!
In menuconfig:
General setup -> IRQ subsystem : Sparse irq numbering should be deactivated. 

This brings back normal temperature and battery life... 
Now, either you recompile a kernel changing this, or you talk about this issue to the official maintenairs of this package... 

awesome find, i guess that slipped under my eyes while i was having a look at those config files.

```
CONFIG_SPARSE_IRQ:                                                                                                                                                  &#9474;  
  &#9474;                                                                                                                                                                     &#9474;  
  &#9474;                                                                                                                                                                     &#9474;  
  &#9474; Sparse irq numbering is useful for distro kernels that want                                                                                                         &#9474;  
  &#9474; to define a high CONFIG_NR_CPUS value but still want to have                                                                                                        &#9474;  
  &#9474; low kernel memory footprint on smaller machines.                                                                                                                    &#9474;  
  &#9474;                                                                                                                                                                     &#9474;  
  &#9474; ( Sparse irqs can also be beneficial on NUMA boxes, as they spread                                                                                                  &#9474;  
  &#9474;   out the interrupt descriptors in a more NUMA-friendly way. )                                                                                                      &#9474;  
  &#9474;                                                                                                                                                                     &#9474;  
  &#9474; **If you don't know what to do here, say N.**
```which part of this sentence ubuntu devs didn't understand? :D

---

### Post by sirverdemer on 2011-08-13
Hi guys!
Thanks for the great detective work. I'm also using a sandy bridge processor laptop (Samsung Series 9) was also experiencing video glitches, installed the 3.0 kernel and am getting a pretty loud fan and extremely hot laptop. This is no good, as I recently changed laptops from a Dell XPS1340 to this one because of precisely those problems.
Steven, have you already filed the new bug?
Should I try to do it aswell?

---

### Post by sbraz on 2011-08-13
[]("http://ubuntuforums.org/member.php?u=1397901")wastedtime-fr did a good job but _nobody with the same platform_ could confirm the solution. are you capable of compiling a kernel? :)

i thought... theoretically i could make one for you and steevven1 but i'm not 100% sure it'll work.
 i'm in the middle of a full backup atm, i'll upload a package somewhere soon.

---

### Post by wastedtime-fr on 2011-08-13
> **sbraz said:**
>  but _nobody with the same platform_ could confirm the solution. 
There is strong evidence that this is not platform related, since I was able to reproduce the exact same problem on my hardware...
If you can provide a kernel package, this should be solved :D

---

### Post by sirverdemer on 2011-08-13
Sbraz, if you could provide a kernel package that would be fantastic!
Thank you very much!

---

### Post by sbraz on 2011-08-13
```
  CC [M]  drivers/mtd/redboot.o
  CC [M]  drivers/mtd/ar7part.o
  CC [M]  drivers/mtd/mtdchar.o
  CC [M]  drivers/mtd/mtd_blkdevs.o
  CC [M]  drivers/mtd/mtdblock.o
  CC [M]  drivers/mtd/mtdblock_ro.o
  CC [M]  drivers/mtd/ftl.o
  LD [M]  drivers/mtd/nftl.o
  LD [M]  drivers/mtd/inftl.o
drivers/mtd/inftl.o: final close failed: **No space left on device**
make[3]: *** [drivers/mtd/inftl.o] Error 1
make[2]: *** [drivers/mtd] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-3.0.0/linux-source-3.0.0'
make: *** [debian/stamp/build/kernel] Error 2
root@sbraz-netbook:/usr/src/linux-source-3.0.0/linux-source-3.0.0# 
```
can you belive it? :lolflag:

---

### Post by wastedtime-fr on 2011-08-13
> **sbraz said:**
> ```
 
drivers/mtd/inftl.o: final close failed: **No space left on device**
make[3]: *** [drivers/mtd/inftl.o] Error 1
make[2]: *** [drivers/mtd] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-3.0.0/linux-source-3.0.0'
make: *** [debian/stamp/build/kernel] Error 2
root@sbraz-netbook:/usr/src/linux-source-3.0.0/linux-source-3.0.0# 
```can you belive it? :lolflag:

I can, now you just have to 
```
sudo rm -rf /home
```to make some room (provided you don't have a separate partition for this) :lolflag:

_**(:evil:Newbs, don't run the previous command if you wish to keep your data)**_

---

### Post by sbraz on 2011-08-13
4hours... still compiling. i really need of those 8 core bulldozer cpus soon.

---

### Post by wastedtime-fr on 2011-08-13
> **sbraz said:**
> 4hours... still compiling. i really need of those 8 core bulldozer cpus soon.
Took 3 hours on my dual core AMD E350@1.6GHz
Did you run make -jx with x = cores + 1 ?
Else, it just uses one thread, ie one core for compiling.

---

### Post by sbraz on 2011-08-13
> **wastedtime-fr said:**
> Took 3 hours on my dual core AMD E350@1.6GHz
Did you run make -jx with x = cores + 1 ?
Else, it just uses one thread, ie one core for compiling.
i did mention the -j argument earlier, anyway AMD K125 1.7GHz single core here. :)
i'm not sure about it's good or not to pass -j2 on a single core.
even though, as you might have noticed by looking at my little "build" script i posted earlier, i log how much time takes to build my *customs*, i've never had the chance to compare the timings; i usually call **nice -n 19 ./build** before going to sleep, and i have /sys/devices/system/cpu/cpufreq/ondemand/ignore_nice_load set to 1 by a script i wrote to manage cpu temperature and keep fan at the lowest speed/noise possible because i run folding@home.
to sum it up, i don't really care how much time it takes to compile, but i think my builds takes more or less 45min in single user text mode.
i'll run some tests about multithreaded compiling soon. ;)

---

### Post by sbraz on 2011-08-14
more informations here:
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)

---

### Post by wastedtime-fr on 2011-08-14
> **sbraz said:**
> 
i'm not sure about it's good or not to pass -j2 on a single core.
even though, as you might have noticed by looking at my little "build" script i posted earlier, i log how much time takes to build my *customs*, i've never had the chance to compare the timings; i usually call **nice -n 19 ./build** before going to sleep, and i have /sys/devices/system/cpu/cpufreq/ondemand/ignore_nice_load set to 1 by a script i wrote to manage cpu temperature and keep fan at the lowest speed/noise possible because i run folding@home.
to sum it up, i don't really care how much time it takes to compile, but i think my builds takes more or less 45min in single user text mode.
i'll run some tests about multithreaded compiling soon. ;)
Usually, when you compile lots of tiny c files, it might get you a few % faster to use -j2, but when compiling huge files, it is often a few % slower. If you have HT technology, it might be better though. Never tested this setup.

---

### Post by sbraz on 2011-08-14
it appears there's something i'm missing about compiling as ubuntu-kernel-devs do, as i had some troubles about kernel-headers in the past and i had now.

to sum it up, the installed kernel keeps looking for the headers in the exact path where the source were compiled locally, i've no idea why it's happening. :D
i've prepared a small install/remove scripts to circumvent this issue the easiest way possible, by creating a symlink pointing at where the headers are actually installed.
i've installed the kernel using my script and it's booting correctly.

this is what installing it looks like:
```
root@sbraz-netbook:/home/linux-3.0.1-ubuntu.RENAME# ls
install
linux-firmware-image_3.0.1-nosparseirq-1_amd64.deb
linux-headers-3.0.1-nosparseirq_3.0.1-nosparseirq-1_amd64.deb
linux-image-3.0.1-nosparseirq_3.0.1-nosparseirq-1_amd64.deb
linux-libc-dev_3.0.1-nosparseirq-1_amd64.deb
remove
source
root@sbraz-netbook:/home/linux-3.0.1-ubuntu.RENAME# ./install 
Selecting previously deselected package linux-headers-3.0.1-nosparseirq.
(Reading database ... 166088 files and directories currently installed.)
Unpacking linux-headers-3.0.1-nosparseirq (from linux-headers-3.0.1-nosparseirq_3.0.1-nosparseirq-1_amd64.deb) ...
Setting up linux-headers-3.0.1-nosparseirq (3.0.1-nosparseirq-1) ...
Selecting previously deselected package linux-image-3.0.1-nosparseirq.
(Reading database ... 179478 files and directories currently installed.)
Unpacking linux-image-3.0.1-nosparseirq (from linux-image-3.0.1-nosparseirq_3.0.1-nosparseirq-1_amd64.deb) ...
Setting up linux-image-3.0.1-nosparseirq (3.0.1-nosparseirq-1) ...
 * dkms: running auto installation service for kernel 3.0.1-nosparseirq         
 *       vboxhost (4.0.12)...                                            [ OK ] 
 *       fglrx (8.872)...                                                [ OK ] 
update-initramfs: Generating /boot/initrd.img-3.0.1-nosparseirq
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.1-nosparseirq
Found initrd image: /boot/initrd.img-3.0.1-nosparseirq
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found Windows 7 (loader) on /dev/sda4
done
```

i'm uploading 525.6MB to mediafire as i type. :)

---

### Post by sbraz on 2011-08-14
[SIZE="3"]here's the deal:[/SIZE]

first of all notice that you need a minimum of 3GB of free space in root.

download these four files and put them somewhere safe.
:arrow: [http://www.mediafire.com/?c7ulrztjt3rpdab](http://www.mediafire.com/?c7ulrztjt3rpdab) (170MB)
:arrow: [http://www.mediafire.com/?x6dise3fsjevc87](http://www.mediafire.com/?x6dise3fsjevc87) (170MB)
:arrow: [http://www.mediafire.com/?fvc2nf3vndguevf](http://www.mediafire.com/?fvc2nf3vndguevf) (170MB)
:arrow: [http://www.mediafire.com/?b7v39it5em39n1i](http://www.mediafire.com/?b7v39it5em39n1i) (15.6MB)

while you download these files, please remove any 3.0.0 or 3.0.1 kernel you have installed just in case.

on a terminal, cd to wherever those files are and type
**7z e linux-3.0.1-ubuntu.7z.001**
this will take a few minutes.

now **./install** to install this [COLOR="Red"]**_EXPERIMENTAL UNSUPPORTED_**[/COLOR] kernel (chmod +x ./install if needed)
have a look at the output and post it here if something goes wrong.

now reboot. grub should be updated automatically so it'll show you a new kernel called 3.0.1-nosparseirq; boot it, check **powertop** again and report back if there's any change.



if you want to remove the kernel for any reason just run **sudo ./remove** (chmod +x ./remove if needed)

---

### Post by wastedtime-fr on 2011-08-14
> **sbraz said:**
> [SIZE=3]here's the deal:[/SIZE]

first of all notice that you need a minimum of 3GB of free space in root.

download these four files and put them somewhere safe.
:arrow: [http://www.mediafire.com/?c7ulrztjt3rpdab](http://www.mediafire.com/?c7ulrztjt3rpdab) (170MB)
:arrow: [http://www.mediafire.com/?x6dise3fsjevc87](http://www.mediafire.com/?x6dise3fsjevc87) (170MB)
:arrow: [http://www.mediafire.com/?fvc2nf3vndguevf](http://www.mediafire.com/?fvc2nf3vndguevf) (170MB)
:arrow: [http://www.mediafire.com/?b7v39it5em39n1i](http://www.mediafire.com/?b7v39it5em39n1i) (15.6MB)

while you download these files, please remove any 3.0.0 or 3.0.1 kernel you have installed just in case.

on a terminal, cd to wherever those files are and type
**7z e linux-3.0.1-ubuntu.7z.001**
this will take a few minutes.

now **./install** to install this [COLOR=Red]**_EXPERIMENTAL UNSUPPORTED_**[/COLOR] kernel (chmod +x ./install if needed)
have a look at the output and post it here if something goes wrong.

now reboot. grub should be updated automatically so it'll show you a new kernel called 3.0.1-nosparseirq; boot it, check **powertop** again and report back if there's any change.



if you want to remove the kernel for any reason just run **sudo ./remove** (chmod +x ./remove if needed)

If you have nothing against french, i can suggest dl.free.fr that will provide good hosting for big files. It's free and anonymous and wont try to make you click on stupid stuff to let you download. 
Anyway, congrats for this, :popcorn:
I hope steven will be able to use it, and hopefully enjoy normal performance for a 3 series kernel

---

### Post by steevven1 on 2011-08-15
Holy crap! Thank you ALL (especially sbraz) for your INSANE amount of support. If there is anything I can do to help you please let me know.

I apologize for not having responded for ~3 days. My life has been INSANE lately.

I will try your files, hopefully tomorrow, and report back here so that everyone knows hte result. You can't imagine how grateful I am. My girlfriend and I both just bought these ThinkPad X220s and are both experiencing the issues.

Again, THANK YOU and I will report back!

:D:D:D

---

### Post by eikenberry on 2011-08-16
I am running Debian Testing, which linux-image-3.0.0-1 just entered, and have been having the same issue. I have noticed significantly higher temperatures (>10C higher) and possibly shorter battery life (haven't measured).

I've just recompiled my kernel with a stock debian config except for disabling CONFIG_SPARSE_IRQ to no effect. So as far as I can tell this is not the fix.

BTW. I have a Lenovo X220 w/ an i7-2620M (sandy bridge).

---

### Post by steevven1 on 2011-08-16
eikenberry, that is discouraging to hear. I haven't gotten a chance to try the proposed fix yet, but I still will in the next day.

More importantly than anything, has anyone filed a bug report officially? I attempted to but got lost and was unable to do it. Maybe someone with more bug-filing experience could try? Be sure to link to this thread in your bug report if you do file one.

Alternatively, if someone points me to the correct place to file a bug, I would be happy to do it.

---

### Post by eikenberry on 2011-08-16
> More importantly than anything, has anyone filed a bug report officially?

I'm going to file a bug in the Debian bug tracking system when I get a chance. I'm running 2.6.39 at the moment to avoid the issue and the bug reporting software wants you running the problem kernel when reporting. I'll try to do that tomorrow.

An Ubuntu user might want to file it with the Ubuntu system in Launchpad.

---

### Post by wastedtime-fr on 2011-08-16
> **eikenberry said:**
> I am running Debian Testing, which linux-image-3.0.0-1 just entered, and have been having the same issue. I have noticed significantly higher temperatures (>10C higher) and possibly shorter battery life (haven't measured).

I've just recompiled my kernel with a stock debian config except for disabling CONFIG_SPARSE_IRQ to no effect. So as far as I can tell this is not the fix.

BTW. I have a Lenovo X220 w/ an i7-2620M (sandy bridge).

I didn't say it was the only bug, just that I could reproduce the wake up calls (hundreds per second) by activating this, but on different hardware. It may be a combination of this flag deactivated + what has been proposed so far (max cpus, etc...) that didn't work alone. Then, debian may have other funky stuff activated by default (or not) that ubuntu. Steveen, please let us know if sbraz's kernel works out for you...

---

### Post by eikenberry on 2011-08-16
Just found some more information on this. Discussions on other forums, but there are alternative solutions proposed. The primary solution offered seems to be adding this to your kernel parameters...

  i915.i915_enable_rc6=1

Here's a list of the sources for this that you can read for more discussion/context. I'm unable to test it right now but thought I'd pass it along.

Sources:
[http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-19.html](http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-19.html)
[https://bbs.archlinux.org/viewtopic.php?pid=974592](https://bbs.archlinux.org/viewtopic.php?pid=974592)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

---

### Post by eikenberry on 2011-08-17
> i915.i915_enable_rc6=1

This was it. After rebooting with this kernel param my temperatures were lower than ever. Batter life seems at least as good as before.

---

### Post by sbraz on 2011-08-17
> **eikenberry said:**
> > i915.i915_enable_rc6=1

This was it. After rebooting with this kernel param my temperatures were lower than ever. Batter life seems at least as good as before.
these is very good news. :)

unfortunately this did not solve steevven1's problems. :(
[http://ubuntuforums.org/showpost.php?p=11141622&postcount=24](http://ubuntuforums.org/showpost.php?p=11141622&postcount=24)

---

### Post by sirverdemer on 2011-08-17
Hi!
I tried the i915.i915_enable_rc6=1 and run powertop. The result is that I get better battery life, but not as good as with the 2.6.38 kernel.
Powertop tells me that, under 2.6.38 I get 9.8W, with Firefox open. Under 3.0 without thei915 setting, I get 15.3 W, while with it on I get 13.9 W. the machine is noticeably quieter, but still louder than with the 2.6.38 kernel... this is really strange.
Now, I will try the kernel you've put up here both with and without... hope that will work.
Thanks guys!

---

### Post by wastedtime-fr on 2011-08-17
> **sbraz said:**
> these is very good news. :)

unfortunately this did not solve steevven1's problems. :(
[http://ubuntuforums.org/showpost.php?p=11141622&postcount=24](http://ubuntuforums.org/showpost.php?p=11141622&postcount=24)

Isn't it a combination of new kernel + some boot time parameters that solved the problem?
Eikenberry, can you let us know?

Also, we have no news from steevven1 ?

---

### Post by eikenberry on 2011-08-17
> **wastedtime-fr said:**
> Isn't it a combination of new kernel + some boot time parameters that solved the problem?
Eikenberry, can you let us know?

I'm running linux-image-3.0.0-1-amd64 (debian testing) with the kernel parameters "quiet pcie_aspm=force i915.i915_enable_rc6=1". I had pcie_aspm=force previously though by itself it made no difference with the problems I was having with the 3.0 kernel. I was seeing idle temperatures of around 50C w/ 3.0 vs 36C w/ 2.6.39. After adding i915.i915_enable_rc6=1 temperatures went back to normal and maybe even slightly lower. My system is an lenovo x220 with the i7.

I haven't been able to test wattage as I don't seem to get this display w/ powertop and there is no /proc/acpi/battery 'directory' to look at. I checked with it unplugged and I have acpid running. Is there some kernel module I'm missing that is needed to get this info? I'd be curious as to the actual watts vs just the temperatures.

---

### Post by wastedtime-fr on 2011-08-17
> **eikenberry said:**
> I'm running linux-image-3.0.0-1-amd64 (debian testing) with the kernel parameters "quiet pcie_aspm=force i915.i915_enable_rc6=1". I had pcie_aspm=force previously though by itself it made no difference with the problems I was having with the 3.0 kernel. I was seeing idle temperatures of around 50C w/ 3.0 vs 36C w/ 2.6.39. After adding i915.i915_enable_rc6=1 temperatures went back to normal and maybe even slightly lower. My system is an lenovo x220 with the i7.

I haven't been able to test wattage as I don't seem to get this display w/ powertop and there is no /proc/acpi/battery 'directory' to look at. I checked with it unplugged and I have acpid running. Is there some kernel module I'm missing that is needed to get this info? I'd be curious as to the actual watts vs just the temperatures.

Ok, so debian kernel + boot params is working OK. 
Can you upload the config file for the debian kernel that is working for you so we can see the difference with the ubuntu one? 
And for the battery info, hasn't that been moved in the "class" directory of (not too sure, not on my machine now) /proc or other special mount fs ?

---

### Post by eikenberry on 2011-08-17
> **eikenberry said:**
> I haven't been able to test wattage as I don't seem to get this display w/ powertop and there is no /proc/acpi/battery 'directory' to look at.

Didn't realize but proc/acpi is deprecated and debian ships with it disabled in their default kernel. There are other ways I'm looking into described in thinkwiki; [http://www.thinkwiki.org/wiki/How_to_measure_power_consumption](http://www.thinkwiki.org/wiki/How_to_measure_power_consumption)

After work I'll try those and see if I can get some wattage measurements to post.

---

### Post by eikenberry on 2011-08-18
> **wastedtime-fr said:**
> Ok, so debian kernel + boot params is working OK. 
Can you upload the config file for the debian kernel that is working for you so we can see the difference with the ubuntu one? 
And for the battery info, hasn't that been moved in the "class" directory of (not too sure, not on my machine now) /proc or other special mount fs ?

The config is the stock debian kernel config, though I've still attached it for convenience.

Using /sys/class/power_supply/BAT0/power_now as a bases I've done a bit of comparison. When left idle with all power saving settings being equal and assuming I're reading power_now right, 3.0 seems to use about .2-.3 more watts than 2.6.39. This might be due to the fan which would eventually spin down to stop on 2.6.39 and would continue to spin on 3.0 (which also might explain the slightly lower temps).

---

### Post by steevven1 on 2011-08-18
> **wastedtime-fr said:**
> Also, we have no news from steevven1 ?

I'm sorry. I am busy both with work and with other, more pressing computer issues right now. I still haven't been able to try the kernel. I do have it saved on my hard drive, and I still plan to try it unless there is some better solution proposed by the time I'm able to.

Some of the recent comments suggest that there may be some other issue at work here? I don't understand a lot of what's been said since the last time I posted in this thread :-/

Let me know if trying sbraz's kernel from post #62 is still a helpful thing to do and report back on.

---

### Post by sbraz on 2011-08-18
hey sorry for my silence i'm still following the topic, it's just that i'm busy trying linux mint debian edition... it's a total mess... very funny! :D

---

### Post by steevven1 on 2011-08-21
Any news on this? If all goes well, I'll be trying the new kernel (by sbraz) in 24 hours.

---

### Post by theskin on 2011-08-21
I have an Asus X53 notebook with intel B940 sandybridge cpu . I used the battery care app with windows 7 to compare power draw and temps against ubuntu 11.04 using kernel 3 .

windows 7 says discharge rate is around 14-15 watts , same as ubuntu . The temperature on the other hand is hovering about 55c under windows and 45c under ubuntu .

I'm happy with those figures :)

---

### Post by steevven1 on 2011-08-22
> **sbraz said:**
> [SIZE=3]here's the deal:[/SIZE]

first of all notice that you need a minimum of 3GB of free space in root.

download these four files and put them somewhere safe.
:arrow: [http://www.mediafire.com/?c7ulrztjt3rpdab](http://www.mediafire.com/?c7ulrztjt3rpdab) (170MB)
:arrow: [http://www.mediafire.com/?x6dise3fsjevc87](http://www.mediafire.com/?x6dise3fsjevc87) (170MB)
:arrow: [http://www.mediafire.com/?fvc2nf3vndguevf](http://www.mediafire.com/?fvc2nf3vndguevf) (170MB)
:arrow: [http://www.mediafire.com/?b7v39it5em39n1i](http://www.mediafire.com/?b7v39it5em39n1i) (15.6MB)

while you download these files, please remove any 3.0.0 or 3.0.1 kernel you have installed just in case.

on a terminal, cd to wherever those files are and type
**7z e linux-3.0.1-ubuntu.7z.001**
this will take a few minutes.

now **./install** to install this [COLOR=Red]**_EXPERIMENTAL UNSUPPORTED_**[/COLOR] kernel (chmod +x ./install if needed)
have a look at the output and post it here if something goes wrong.

now reboot. grub should be updated automatically so it'll show you a new kernel called 3.0.1-nosparseirq; boot it, check **powertop** again and report back if there's any change.



if you want to remove the kernel for any reason just run **sudo ./remove** (chmod +x ./remove if needed)


Okay, I attempted to install this. I received an error relating to disk space. Here are the error messages from running "install"

```
update-initramfs: Generating /boot/initrd.img-3.0.1-nosparseirq
gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.0.1-nosparseirq
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
...
dpkg: error processing linux-image-3.0.1-nosparseirq (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.0.1-nosparseirq

```

I'm not sure why I wouldn't have enough space...Where is it trying to write to? "df -h" yields:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/steven-root
                      290G  143G  133G  52% /
none                  1.9G  696K  1.9G   1% /dev
none                  1.9G  124K  1.9G   1% /dev/shm
none                  1.9G  108K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda1             228M  119M   98M  55% /boot

```

Help? :-/

---

### Post by sbraz on 2011-08-22
> **steevven1 said:**
> I'm not sure why I wouldn't have enough space...Where is it trying to write to? "df -h" yields:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/steven-root
                      290G  143G  133G  52% /
none                  1.9G  696K  1.9G   1% /dev
none                  1.9G  124K  1.9G   1% /dev/shm
none                  1.9G  108K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
**/dev/sda1             228M  119M   98M  55% /boot**

```

Help? :-/
i'm a big fan of the separate /boot from / (dunno why, i just do), but 228MB is too low even for my standards. 500MB-1GB just be enough to test (resize it back after it's installed).

consider this is not a kernel compiled by ubuntu's book, so there might be some differences the way it installs.
update-initramfs is the second-last operation which the installer does (the last one is update-grub), so the kernel installs correctly, you just need more space in sda1.

---

### Post by steevven1 on 2011-08-22
Aha. You had written "root" in your original message instead of "boot." Thank you.

The reason I have a separate /boot is because I have encrypted LVM set up...This could be complicated to resize :-/

---

### Post by sbraz on 2011-08-22
LVM? never used it so i don't know how.

anyway, it is possible that you can simply remove some unused kernels to make some space (leave at least one 100% working!!), btw there shouldn't be 119MB used, i have 3 kernels installed and the whole /boot is  46.7 MB atm. but then again i'm no LVM-expert so there might be a reason. :)

---

### Post by steevven1 on 2011-08-22
Okay, I did exactly that (removing old kernels to make room), and installed your kernel successfully.

The result: **"[Rescheduling interrupts] <kernel IPI>"** has disappeared from powertop output, and CPU wakeups are about the same as with the 2.6.10 kernel! Hooray!

The problem: Battery life has only improved marginally compared to the stock Ubuntu 3-series kernels. There must be another problem other than this "rescheduling interrupt."

Here is my battery life in hours with each kernel under normal use (same screen brightness, wifi, processor load, etc), approximately:
Kernel 2.6.10 - 6.2 hours
Kernel 3.0 (Ubuntu debs) - 4.0 hours
Kernel 3.0 (sbraz modified) - 4.6 hours

So THANK YOU sbraz for your significant contribution, but obviously this was only part of the problem. I tried adding "i915.i915_enable_rc6=1" to the kernel boot parameters, and it had absolutely no effect. If anything, it actually made power consumption worse.

Ideas? :-/

---

### Post by sbraz on 2011-08-22
> **steevven1 said:**
> The result: "[Rescheduling interrupts] <kernel IPI>" has disappeared from powertop output, and CPU wakeups are about the same as with the 2.6.10 kernel! [B]Hooray!
[/B]
The problem: Battery life has only improved marginally compared to the stock Ubuntu 3-series kernels. There must be another problem other than this "rescheduling interrupt."

Here is my battery life in hours with each kernel under normal use (same screen brightness, wifi, processor load, etc), approximately:
[B]Kernel 2.6.10 - 6.2 hours
Kernel 3.0 (Ubuntu debs) - 4.0 hours
Kernel 3.0 (sbraz modified) - 4.6 hours[/B]

So THANK YOU sbraz for your significant contribution, but obviously this was only part of the problem. I tried adding "i915.i915_enable_rc6=1" to the kernel boot parameters, and it had absolutely no effect. If anything, it actually made power consumption worse.

Ideas? :-/
Hooray indeed! XD

what about testing "Kernel 3.0 (sbraz modified) **with pcie_aspm=force kernel parameter** - ??? hours"?

---

### Post by steevven1 on 2011-08-22
> **sbraz said:**
> 
what about testing "Kernel 3.0 (sbraz modified) **with pcie_aspm=force kernel parameter** - ??? hours"?


Same as without that kernel parameter, but good idea. Any more ideas?

Also, to those of you that filed bug reports, what has been the response? Links?

---

### Post by sbraz on 2011-08-23
3.0.3 oneiric is out:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.3-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.3-oneiric/)

---

### Post by steevven1 on 2011-08-23
> **sbraz said:**
> 3.0.3 oneiric is out:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.3-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.3-oneiric/")

I actually already tried 3.1rc2 with no improvement. I guess I can try 3.0.3 when I have some time, but it almost seems like a waste. Might as well try everything, I suppose.

---

### Post by sbraz on 2011-08-23
okay. at this point someone (all of you who have this issues) should post a bug report at bugs.launchpad.net

---

### Post by steevven1 on 2011-08-23
I have tried multiple times to report a bug, but can't. All I can find is this USELESS guide: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Is this seriously the ONLY way to report a bug? I can't just fill out a form somewhere without running software to do it? When I try to do it the way explained in the guide, it tells me that I'm using a stable version of Xubuntu, and that only people running dev versions (like 11.10) can report bugs. Wtf?

---

### Post by steevven1 on 2011-08-23
Well, I fired an email off to the Linux kernel developers mailing list, since this seems to be a kernel bug. That seems to be a pretty direct route of attack. I'd still like to file the bug in LaunchPad though, so if anyone has advice on how to do that (read my post directly above this one to see the problems I ran into), I'm all ears.

---

### Post by sbraz on 2011-08-23
honestly that guide sounds a little too long.

1. register to launchpad.net
2. go here [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)
3. read and fill the form:

In what package did you find this bug? --> linux-image-3.0-0-generic

Further information: --> your problem. include the link to this discussion.
this one link ([http://ubuntuforums.org/showthread.php?t=1822629](http://ubuntuforums.org/showthread.php?t=1822629))

Extra options: attach what's needed. :)



notice that you can use **ubuntu-bug linux** to ease the process but first uninstall my kernel or you'll see this message:
```
The problem cannot be reported:

This is not a genuine Ubuntu package
```
followed by the name of the core package you installed manually.

---

### Post by steevven1 on 2011-08-23
Thank you! I knew there must have been a simple form somewhere! I'll file the bug report in the next 24 hours. Also, the Linux kernel team (via kernel.org) is actually already communicating with me via email. Apparently they think this really may be a genuine, new bug in the kernel, as we suspected.

Progress!

---

### Post by steevven1 on 2011-08-24
It appears that Phoronix has also found our bug! They mention that it specifically affects Sandy Bridge laptops.

"Besides the new [Linux 3.1 kernel]("http://www.phoronix.com/scan.php?page=search&q=Linux+3.1") power regression, there's also  a power regression introduced in the Linux 3.0 kernel that has previously not  been talked about on Phoronix. The Linux 3.0 power draw is up by 24% over the  Linux 2.6.39 kernel."

[http://www.phoronix.com/scan.php?page=article&item=linux_31_power_regress&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_31_power_regress&num=1)

Although they offer no solution yet, it is very encouraging to see that others have noticed our (apparently) exact same problem.

EDIT: Haven't tried these yet, but here are some other suggested tweaks: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

---

### Post by steevven1 on 2011-08-25
Okay, I tried the Phoronix tweaks with sbraz's nosparseirq kernel. Here were the results:

[B]i915.i915_enable_rc6=1 - No/negligible effect

[/B][B]i915.i915_enable_fbc=1 - No/negligible effect

[/B]**i915.lvds_downclock=1 - ****No/negligible effect**

---

### Post by steevven1 on 2011-08-25
Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+bug/834037](https://bugs.launchpad.net/ubuntu/+bug/834037)

If you could all click on "Does this bug affect you?" and register that it affects you, that would be great. Thanks.

---

### Post by steevven1 on 2011-09-01
I made a mistake previously and would like to clear it up. The mistake  was a result of not giving something enough time and testing. I have now  tested it more thoroughly and have more to report:

Using the modified (no sparse irq) kernel with kernel parameter i915.i915_enable_rc6=1 DOES increase battery life compared to without that kernel parameter. The only problem is that it also brings back the graphical glitches and freezes, which were the ONLY reason I wanted to switch to kernel 3.x in the first place. Thus, that kernel parameter in concert with disabling sparse irq in the kernel solves the power problem (completely or almost completely), but the i915.i915_enable_rc6=1 kernel parameter brings back the glitchy graphics from kernel 2.6.x.

---

### Post by chazinams on 2011-09-23
Has anyone compared ubuntu-11.10 power consumption to windows-7?

I've read a lot about how ubuntu keeps gaining power regressions with new kernel releases. How Natty (and now Oneiric) runs hot and uses lots of power. But I read this report at Phoronix ([http://www.phoronix.com/scan.php?page=article&item=windows_ubuntu_pow&num=1](http://www.phoronix.com/scan.php?page=article&item=windows_ubuntu_pow&num=1)) and ubuntu looked pretty much even with Windows-7 except for some of the video playback.

Having some sort of standard to compare this increased Sandy Bridge power use to would help me understand how severe the issue is. I was planning on running ubuntu-11.10 on a new Lenovo X220. But the X220 will be used on the road and battery life is extremely important so I might need to use Windows-7 for the time being depending on how bad the issue is when compared to windows-7.

---

### Post by steevven1 on 2011-09-23
> **chazinams said:**
> Has anyone compared ubuntu-11.10 power consumption to windows-7?

I've read a lot about how ubuntu keeps gaining power regressions with new kernel releases. How Natty (and now Oneiric) runs hot and uses lots of power. But I read this report at Phoronix ([http://www.phoronix.com/scan.php?page=article&item=windows_ubuntu_pow&num=1](http://www.phoronix.com/scan.php?page=article&item=windows_ubuntu_pow&num=1)) and ubuntu looked pretty much even with Windows-7 except for some of the video playback.

Having some sort of standard to compare this increased Sandy Bridge power use to would help me understand how severe the issue is. I was planning on running ubuntu-11.10 on a new Lenovo X220. But the X220 will be used on the road and battery life is extremely important so I might need to use Windows-7 for the time being depending on how bad the issue is when compared to windows-7.

My experience on my X220 with the Sandy Bridge i7 is that on kernel 2.6.x (default on 11.04), Ubuntu uses the same amount of power as Windows 7 and gets GREAT battery life (7+ hours with 6-cell battery), but kernel 2.6.x on this processor suffers unacceptable graphical glitches which appear on and off, and occasionally even freezes completely.

With kernel 3.x (default on 11.10), my X220 has no problems with graphics or freezing AT ALL, but the battery lasts 4 hours flat and the computer is noticeably warmer.

Huge bummer. Hope this gets fixed very soon.

---

### Post by steevven1 on 2011-09-23
Looks like Phoronix is seeing the exact same thing on Sandy Bridge: [http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg)

---

### Post by chazinams on 2011-09-23
> **steevven1 said:**
> 

Huge bummer. Hope this gets fixed very soon.

I fear it will be a while. The Natty power bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)) was marked High Importance and a fix was just committed a day or two ago. This bug is marked Medium/Undecided.

Gotta wonder about Linus and his kernel people. Don't they care about power use? Hard to believe in this day and age it's not a high priority in design.

I'm figuring the best we can hope for will be 12.04. I'm prolly gonna have to use stinkin' Windows-7 for the road :(

---

### Post by razorxpress on 2011-09-26
I had posted [Ubuntu 11.04 sandy bridge support]("http://ubuntuforums.org/showthread.php?t=1817374"). I did not know this post, so sorry guys for being late. I have dual graphics card, so the problem is even dreadful than having integrated card of sandy bridge. I even posted a [kernel bug]("https://bugzilla.kernel.org/attachment.cgi?id=70942") (server is down for now). All my games run pretty good on kernels above 2.38, but 2.38 is the coolest one (with coretemp installed), however there is a terrible glitch with this kernel and I have to play most of the games in window mode and very small screen. I play alien-arena even on those glitch. Since I use xorg-edgers repo for xorg and xserver, I have seen growth of graphics but it is still very bad when using 2.38 kernel. If things go this way I even have to install 2.38 kernel in oneric. I don't know how the power regression keeps on increasing. Are they trying to support something extraordinary or are they going back to server mode leaving Desktop as it was in old days. If we have to blame anyone it is Intel guys. But blaming someone would not solve the problem. Problem with enabling any options to kernel is not good? My computer won't boot if I don't put acpi_osi=linux pci=noacpi on kernel option. All of this disability has to do with GPU. If we don't put some wierd options on kernel line then the computer generates black screen of death and does not boot.

---

### Post by chazinams on 2011-09-27
Guys, update Oneiric and recheck power usage. An Oneiric fix has been released for the "Natty" power bug.

Hopefully, it helps improve the power issue in Oneiric to some extent.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by sbraz on 2011-09-28
thanks for reporting these good news. :)

however:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/178](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/178)
```
The patch noted in comment #164 was applied to Oneiric when the Oneiric kernel was
 rebased to upstream stable v3.0.1. It was subsequently uploaded and available in 
Oneiric as of linux-3.0.0-8.10. I'm therefore marking the Oneiric task Fix Released. 
[B]If you are still experiencing issues with regards to power consumption even with 
this patch applied, I strongly urge you to open a new bug report as issues such as 
this are typically hardware specific and will require different fixes.[/B] Thanks.
```

here's post #164:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/164](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/164)
```

Tim Gardner (timg-tpi) wrote on 2011-09-20:	 #164
SRU Justification:

Impact: Since 2.6.36 (23016bf0d25), Linux prints the existence of "epb" in /proc/cpuinfo,
    Since 2.6.38 (d5532ee7b40), the x86_energy_perf_policy(8) utility has
    been available in-tree to update MSR_IA32_ENERGY_PERF_BIAS.

    However, the typical BIOS fails to initialize the MSR, presumably
    because this is handled by high-volume shrink-wrap operating systems...

    Linux distros, on the other hand, do not yet invoke x86_energy_perf_policy(8).
    As a result, WSM-EP, SNB, and later hardware from Intel will run in its
    default hardware power-on state (performance), which assumes that users
    care for performance at all costs and not for energy efficiency.
    While that is fine for performance benchmarks, the hardware's intended default
    operating point is "normal" mode...

    Initialize the MSR to the "normal" by default during kernel boot.

    x86_energy_perf_policy(8) is available to change the default after boot,
    should the user have a different preference.

Patch: commit abe48b108247e9b90b4c6739662a2e5c765ed114 upstream

Changed in linux (Ubuntu Natty):
assignee:	 Canonical Kernel Team (canonical-kernel-team) &#8594; Tim Gardner (timg-tpi)
status:	 Confirmed &#8594; In Progress
```



meanwhile... kernel.org has been down for 20 days now. :(

---

### Post by steevven1 on 2011-10-03
I'll be installing Xubuntu 11.10 the day the official, stable release comes out, and I'll report on power usage here shortly after that. Sounds like SOMETHING has been done, but probably not a fix for the specific bug we're talking about here, which SEEMS to be related to graphics drivers.

---

### Post by sbraz on 2011-10-04
isn't there a live 11.10 beta somewhere?

---

### Post by Suhel28 on 2011-10-06
I've installed Ubuntu 11.10 beta yesterday and man it sucks battery power like a sponge would suck water, I hardly get an hour backup and what do I do?? only surfing..

My laptop got 6 cell battery and its just 5months old, on Natty the battery used to last more than two hours but Ocelot 

~back to windows 7~ till this bug is fixed. I was really hoping to switch to Ubuntu :(

---

### Post by vdpr on 2011-10-08
> ~back to windows 7~ till this bug is fixed.

Yep, sadly I'm on the same boat... Low battery life is simply not acceptable!

---

### Post by Suhel28 on 2011-10-08
> **vdpr said:**
> Yep, sadly I'm on the same boat... Low battery life is simply not acceptable!
 Yesterday I played FIFA 10 on windows 7 for 45 minutes (this game is a battery killer trust me) after quitting the game I'd around 45% battery after that I switched to video surfing and watched videos for around 1.30 hours and when I saw the battery it was still 7% so let me sum up 1 hour (45+30)mins. = 2 hours 15 minutes and my laptop was still on
 
on 11.10 I'd 100% (it showed 1 hr 12 mins the battery will last wtf) when started. I started surfing 15-20 minutes and I saw battey it dropped to 20 mins after few more minutes of surfing I'd critically low battery warning 
 
thats pathetic

---

### Post by Suhel28 on 2011-10-08
> **vdpr said:**
> Yep, sadly I'm on the same boat... Low battery life is simply not acceptable!

Just reade bout the bug, its a kernel issue and they've no plan of fixing it. There is a work around for it but still the battery life decreases

End of story, no more Linux for me

Back to full time WINDOWS I don't want my laptop battery to die

---

### Post by BazookaAce on 2011-10-11
Installed 11.10 today and man is the battery jumping around. I charged the battery up to 100%, unplugged it, it says i have 1 hour 50 minutes left. 5 minutes later it says i have 33 minutes left with 85% battery left, and now 5 minutes later again it says now that i have 1 hours 40 minutes left. What in the hell is up?

---

### Post by tushantin on 2011-10-13
HP Mini with Intel Atom. 

And I'm having the same issue everyone's having...

---

### Post by BlueHacker1111 on 2011-10-15
> **tushantin said:**
> HP Mini with Intel Atom. 

And I'm having the same issue everyone's having...

Are you using Sandy Bridge chip? When did you buy the netbook? As far as I know, Sandy Bridge technology is not available until January 2011. Meaning that any netbooks before that date did not use Sandy Bridge technology, and so should not be effected by this power regression.

---

### Post by tushantin on 2011-10-15
> **BlueHacker1111 said:**
> Are you using Sandy Bridge chip? When did you buy the netbook? As far as I know, Sandy Bridge technology is not available until January 2011. Meaning that any netbooks before that date did not use Sandy Bridge technology, and so should not be effected by this power regression.
I wasn't aware that Intel Atom also included Sandy Bridge technology...
 
I use HP Mini 210. You may check it out here: [http://reviews.cnet.com/laptops/hp-mini-210-hd/4505-3121_7-33939694.html](http://reviews.cnet.com/laptops/hp-mini-210-hd/4505-3121_7-33939694.html)

Considering it was out at 2010, there's a good chance it doesn't include Sandy Bridge.

---

### Post by steevven1 on 2011-10-16
Installed Xubuntu 11.10 today. Looks like the same old story, which was expected since 11.10 uses the 3.0 kernel.

---

### Post by crysman on 2011-10-18
> **steevven1 said:**
> Installed Xubuntu 11.10 today. Looks like the same old story, which was expected since 11.10 uses the 3.0 kernel.

For my ASUS U36S [worked the i915 trick]("http://ubuntuforums.org/showpost.php?p=11363322&postcount=142") in GRUB on Xubuntu 11.10 - I am right now already on á 4 hours uptime, still having 25% battery left..

---

### Post by kuric on 2011-10-19
There's no use. Linux never had good battery performance on my machines but this time is worse than ever. High energy consumption and high temperatures. This is major issue to me, battery autonomy is **_essential_**.

---

### Post by crysman on 2011-10-23
> **crysman said:**
> For my ASUS U36S [worked the i915 trick]("http://ubuntuforums.org/showpost.php?p=11363322&postcount=142") in GRUB on Xubuntu 11.10 - I am right now already on á 4 hours uptime, still having 25% battery left..

OK, I have achieved only 9W power drain (measured with *PowerTOP 1.97b1*) on my ASUS U36SD machine (Xubuntu 11.1O, kernel 3.0.0-12). This means about 6 hours on battery with occasional WiFi - I've not yet tested that fully. The point is that without i915-like boot options and without this script, I had more than 20 Watts!

I wrote a script to do all the stuff needed (except of needed boot options of course). This script should not do any persistent changes. Thanks to all active people and Internet sources for their great help!

Here it is:
```

#! /bin/bash
# power adjustments for maximum battery life on ASUS U36SD notebook
# crysman(c)2011-10

echo ">>This script is originally written for ASUS U36SD notebooks, using kernel 3.0.0-12."
echo ">>I highly reccommend to boot with i915.i915_enable_rc6=1 option, it saves a lot of Watts and puts system temperature back to normal level (50°) as with 2.6.38-12 kernel."
echo ">>You need acpi_call installed somewhere and edit the path to it in this script."
sudo echo "--"

#------------------------------------- variables()
#modify here, no slash at the end
ACPI_CALL_DIR='/home/crysman/acpi_call'
NTPSERVER='ntp.ubuntu.com'

#------------------------------------- functions()
function OK() {
	if [ "$1" != "" ]; then 	
		echo -e "\e[1;32m  OK\e[0m ($1)"
	else
		echo -e "\e[1;32m  OK\e[0m"
	fi
}

function ERR(){
	if [ "$1" != "" ]; then
		echo -e "\e[1;31m  FAIL\e[0m ($1)"
	else
		echo -e "\e[1;31m  FAIL\e[0m"
	fi
}

function showexitstatus(){
#do not add any command before the if statement!
  if [ $? -eq 0 ]; then
    OK
  else
    ERR
  fi
}

#--------------------------------- main()
#laptop_mode
echo ">>checking if laptop_mode is activated..."
if [ `cat /proc/sys/vm/laptop_mode` -eq 5 ]; then
	OK "already set to 5, nothing to do here"
else
	ERR "not activated, setting it to 5..."
	sudo sh -c 'echo 5 > /proc/sys/vm/laptop_mode'
	showexitstatus
fi

#audio
#mute
#TODO buggy!! see powertop
#echo ">>muting sound..."
#amixer set Master mute > /dev/null
#showexitstatus

echo ">>enabling power savings for sound card..."
sudo sh -c 'echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller'
sudo sh -c 'echo 1 > /sys/module/snd_hda_intel/parameters/power_save'
showexitstatus

#LCD brightness
echo ">>setting brightness level to 1..."
sudo sh -c 'for i in /sys/class/backlight/acpi_video*/brightness; do echo -n 1 > $i; done'
showexitstatus

#dedicated graphic card
echo ">>switching off the Nvidia dedicated card..."
if lsmod | grep '^acpi_call' > /dev/null; then
	OK "acpi_call.ko already present in kernel, not inserting"
else
	echo "  >>inserting acpi_call.ko into kernel"	
	sudo insmod $ACPI_CALL_DIR/acpi_call.ko
	showexitstatus
fi
sudo $ACPI_CALL_DIR/test_off.sh
showexitstatus

#CPU
# Select Ondemand CPU Governor
echo ">>activating ondemand CPU governor"
sudo sh -c 'for i in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo ondemand > $i; done'
showexitstatus

#multi-threading scheduler tunable
echo ">>enabling multi-threading sheduler"
sudo sh -c "echo 1 > /sys/devices/system/cpu/sched_mc_power_savings"
showexitstatus

#harddisk tweaks
echo ">>setting up the SATA link Power management to min_power..."
sudo sh -c 'for i in /sys/class/scsi_host/host*/link_power_management_policy; do echo min_power > $i; done'
showexitstatus

echo ">>reducing dirty page (VM) writebacks to 1500cs..."
sudo sh -c 'echo 1500 > /proc/sys/vm/dirty_writeback_centisecs'
showexitstatus

#autosuspend devices
echo ">>setting up USB auto power levels..."
sudo sh -c 'for i in /sys/bus/usb/devices/*/power/level; do echo auto > $i; done'
showexitstatus

echo ">>setting up autosuspend for USB devices..."
sudo sh -c 'for i in /sys/bus/usb/devices/*/power/autosuspend; do echo 1 > $i; done'
showexitstatus

echo ">>setting up autosuspend for PCI devices..."
sudo sh -c 'for i in /sys/bus/pci/devices/*/power/control; do echo auto > $i; done'
showexitstatus

#ntpd
echo ">>syncing system time and stopping ntpd..."
sudo service ntp stop
sudo ntpdate $NTPSERVER
showexitstatus

#networking
echo ">>activate wireless power saving mode with 500ms..."
sudo iwconfig wlan0 power timeout 500ms
showexitstatus

echo -e '>>reducing wireless adapter power to 5\n  ("sudo iwconfig wlan0 txpower auto" to revert) ...'
sudo iwconfig wlan0 txpower 5
showexitstatus

echo ">>disabling wake-on-LAN..."
sudo ethtool -s eth0 wol d
showexitstatus

#bluetooth
echo '>>switching off bluetooth...'
#sudo ifdown eth1
ERR "not yet implemented :( please, do it manually"
#showexitstatus

echo '>>disabling networking...'
ERR "not yet implemented :( please, do it manually"
#showexitstatus


```

If you upgrade something, please, make it public here ;)

-- crysman

---

### Post by sbraz on 2011-10-23
very nice script, thank you.

> sh -c 'echo 1500 > /proc/sys/vm/dirty_writeback_centisecs'
i've found that this setting might cause troubles while transferring large (4-500MB+) files through samba: the copy process just hung and it couldn't complete even retrying many times, and after it hung i had to remount the remote samba share and eventually reboot the whole system.
the default value for this is 500msec.

---

### Post by steevven1 on 2011-10-24
Linux kernel 3.1 (stable) was released today. Anybody test it with Sandy Bridge for battery life WITHOUT enabling i915rc6 (since it causes graphical glitches and freezes for many people)?

Just curious if there is any improvement. I have been told recently that Intel is working on the problem.

---

### Post by linuxuser12345 on 2011-10-24
Don't worry: you are not alone.
[http://ubuntuforums.org/showthread.php?t=1865832](http://ubuntuforums.org/showthread.php?t=1865832)
[http://askubuntu.com/questions/70877/battery-critically-low-at-85](http://askubuntu.com/questions/70877/battery-critically-low-at-85)

---

### Post by Bucic on 2011-10-24
W...T...F?!
I recall I read about this issue a year ago or so and it hasn't been fixed yet?!


> **steevven1 said:**
> Linux kernel 3.1 (stable) was released today. Anybody test it with Sandy Bridge for battery life WITHOUT enabling i915rc6 (since it causes graphical glitches and freezes for many people)?

Just curious if there is any improvement. I have been told recently that Intel is working on the problem.
Some info [http://www.h-online.com/open/features/What-s-new-in-Linux-3-1-1347364.html](http://www.h-online.com/open/features/What-s-new-in-Linux-3-1-1347364.html)

---

### Post by crysman on 2011-10-24
> **crysman said:**
> OK, I have achieved only 9W power drain (measured with *PowerTOP 1.97b1*) on my ASUS U36SD machine (Xubuntu 11.1O, kernel 3.0.0-12). This means about 6 hours on battery with occasional WiFi - I've not yet tested that fully. The point is that without i915-like boot options and without this script, I had more than 20 Watts!

I wrote a script to do all the stuff needed (except of needed boot options of course). This script should not do any persistent changes. Thanks to all active people and Internet sources for their great help!

Here it is:
```

#! /bin/bash
# power adjustments for maximum battery life on ASUS U36SD notebook
# crysman(c)2011-10

echo ">>This script is originally written for ASUS U36SD notebooks, using kernel 3.0.0-12."
echo ">>I highly reccommend to boot with i915.i915_enable_rc6=1 option, it saves a lot of Watts and puts system temperature back to normal level (50°) as with 2.6.38-12 kernel."
echo ">>You need acpi_call installed somewhere and edit the path to it in this script."
sudo echo "--"

#------------------------------------- variables()
#modify here, no slash at the end
...
...

```

If you upgrade something, please, make it public here ;)

-- crysman

New version (changelog included):
```

#! /bin/bash
# power adjustments for maximum battery life on ASUS U36SD notebook
# crysman(c)2011-10
# version 1.01

#changelog:
#1.01	+ remount / and /home with relatime option added
#	* ntp part updated to not perform ntpdate when no Internet connection available


echo ">>This script is originally written for ASUS U36SD notebooks, using kernel 3.0.0-12."
echo ">>I highly reccommend to boot with i915.i915_enable_rc6=1 option, it saves a lot of Watts and puts system temperature back to normal level (50°) as with 2.6.38-12 kernel."
echo ">>You need acpi_call installed somewhere and edit the path to it in this script."
sudo echo "--"

#------------------------------------- variables()
#modify here, no slash at the end
ACPI_CALL_DIR='/home/crysman/acpi_call'
NTPSERVER='ntp.ubuntu.com'

#------------------------------------- functions()
function OK() {
	if [ "$1" != "" ]; then 	
		echo -e "\e[1;32m  OK\e[0m ($1)"
	else
		echo -e "\e[1;32m  OK\e[0m"
	fi
}

function ERR(){
	if [ "$1" != "" ]; then
		echo -e "\e[1;31m  FAIL\e[0m ($1)"
	else
		echo -e "\e[1;31m  FAIL\e[0m"
	fi
}

function showexitstatus(){
#do not add any command before the if statement!
  if [ $? -eq 0 ]; then
    OK
  else
    ERR
  fi
}

#--------------------------------- main()
#laptop_mode
echo ">>checking if laptop_mode is activated..."
if [ `cat /proc/sys/vm/laptop_mode` -eq 5 ]; then
	OK "already set to 5, nothing to do here"
else
	ERR "not activated, setting it to 5..."
	sudo sh -c 'echo 5 > /proc/sys/vm/laptop_mode'
	showexitstatus
fi

#audio
#mute
#TODO buggy!! see powertop
#echo ">>muting sound..."
#amixer set Master mute > /dev/null
#showexitstatus

echo ">>enabling power savings for sound card..."
sudo sh -c 'echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller'
sudo sh -c 'echo 1 > /sys/module/snd_hda_intel/parameters/power_save'
showexitstatus

#LCD brightness
echo ">>setting brightness level to 1..."
sudo sh -c 'for i in /sys/class/backlight/acpi_video*/brightness; do echo -n 1 > $i; done'
showexitstatus

#dedicated graphic card
echo ">>switching off the Nvidia dedicated card..."
if lsmod | grep '^acpi_call' > /dev/null; then
	OK "acpi_call.ko already present in kernel, not inserting"
else
	echo "  >>inserting acpi_call.ko into kernel"	
	sudo insmod $ACPI_CALL_DIR/acpi_call.ko
	showexitstatus
fi
sudo $ACPI_CALL_DIR/test_off.sh
showexitstatus

#CPU
# Select Ondemand CPU Governor
echo ">>activating ondemand CPU governor"
sudo sh -c 'for i in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo ondemand > $i; done'
showexitstatus

#multi-threading scheduler tunable
echo ">>enabling multi-threading sheduler"
sudo sh -c "echo 1 > /sys/devices/system/cpu/sched_mc_power_savings"
showexitstatus

#harddisk and filesystem tweaks
echo ">>setting up the SATA link Power management to min_power..."
sudo sh -c 'for i in /sys/class/scsi_host/host*/link_power_management_policy; do echo min_power > $i; done'
showexitstatus

echo ">>reducing dirty page (VM) writebacks to 1500cs..."
sudo sh -c 'echo 1500 > /proc/sys/vm/dirty_writeback_centisecs'
showexitstatus

echo ">>remounting with relatime..."
echo "  /"
sudo mount -o remount,relatime /
showexitstatus
echo "  /home"
sudo mount -o remount,relatime /home
showexitstatus

#autosuspend devices
echo ">>setting up USB auto power levels..."
sudo sh -c 'for i in /sys/bus/usb/devices/*/power/level; do echo auto > $i; done'
showexitstatus

echo ">>setting up autosuspend for USB devices..."
sudo sh -c 'for i in /sys/bus/usb/devices/*/power/autosuspend; do echo 1 > $i; done'
showexitstatus

echo ">>setting up autosuspend for PCI devices..."
sudo sh -c 'for i in /sys/bus/pci/devices/*/power/control; do echo auto > $i; done'
showexitstatus

#ntpd
echo ">>syncing system time and stopping ntpd..."
if sudo service ntp stop 2> /dev/null; then
	if ping $NTPSERVER -c 1 > /dev/null 2>&1; then	
		sudo ntpdate $NTPSERVER
	fi
	showexitstatus
else
  OK "NTP has been not running, no changes needed"
fi


#networking
echo ">>activate wireless power saving mode with 500ms..."
sudo iwconfig wlan0 power timeout 500ms
showexitstatus

echo -e '>>reducing wireless adapter power to 5\n  ("sudo iwconfig wlan0 txpower auto" to revert) ...'
sudo iwconfig wlan0 txpower 5
showexitstatus

echo ">>disabling wake-on-LAN..."
sudo ethtool -s eth0 wol d
showexitstatus

#bluetooth
echo '>>switching off bluetooth...'
#sudo ifdown eth1
ERR "not yet implemented :( please, do it manually"
#showexitstatus

echo '>>disabling networking...'
ERR "not yet implemented :( please, do it manually"
#showexitstatus

```

--crysman

---

### Post by crysman on 2011-10-25
> **sbraz said:**
> very nice script, thank you.


i've found that this setting might cause troubles while transferring large (4-500MB+) files through samba: the copy process just hung and it couldn't complete even retrying many times, and after it hung i had to remount the remote samba share and eventually reboot the whole system.
the default value for this is 500msec.

I cannot say, I am not using samba... I wrote this script to get maximum battery life while travelling (no samba needed :)

--crysman

---

### Post by Bucic on 2011-10-25
After applying all of the known tricks I lowered the power consumption on my both laptops down by just 10% out of ~50% lost when compared to windows! Please support fixing the ****** kernel by voting "this affects me":
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

---

### Post by junkilo on 2011-10-31
getting about an 8w draw on 3/4 brightness on 3.0.0-12 after tweaks. info on my setup [here]("http://ubuntuforums.org/showthread.php?p=11411115")

---

### Post by tushantin on 2011-10-31
But what of Intel Atom? :confused:

Has anybody tested Intel Atom with the latest Kernel (in 11.10) yet?

---

### Post by steevven1 on 2011-10-31
> **junkilo said:**
> getting about an 8w draw on 3/4 brightness on 3.0.0-12 after tweaks. info on my setup [here]("http://ubuntuforums.org/showthread.php?p=11411115")

Virtually all of your power savings are coming from this kernel parameter: i915.i915_enable_rc6=1

This parameter is known to cause graphical glitches and system freezes  on Sandy Bridge processors, just so you know. Are you experiencing any  problems like this?

On my ThinkPad X220 (also with a Sandy Bridge i7), this kernel parameter  causes HUGE power savings and also graphical glitches and freezes.

---

### Post by Bucic on 2011-10-31
> **steevven1 said:**
> Virtually all of your power savings are coming from this kernel parameter: i915.i915_enable_rc6=1

This parameter is known to cause graphical glitches and system freezes  on Sandy Bridge processors, just so you know. Are you experiencing any  problems like this?

On my ThinkPad X220 (also with a Sandy Bridge i7), this kernel parameter  causes HUGE power savings and also graphical glitches and freezes.
I've used all of the known "grub config tricks" and it got me from 75/70 to ~50/50 deg C. No graphical glitches here, Thinkpad T500, but my desktop performance is poor (dragging windows is choppy and CPU intensive, while switching between windows - ultra smooth), _same as before I used the tricks._

EDIT:
> **tushantin said:**
> But what of Intel Atom? :confused:

Has anybody tested Intel Atom with the latest Kernel (in 11.10) yet?
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_power&num=6](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_power&num=6)

---

### Post by Bucic on 2011-11-01
3.1 kernel didn't help. I've just tried 2.6.32 and 34. I didn't notice any difference in temperatures. They were still high. Much higher than on windows. Really weird as the power regressions (few of them) started no sooner than from 2.6.35, AFAIK.

---

### Post by steevven1 on 2011-11-11
Apparently, a big power bug has been fixed in the Linux kernel: [http://linux.slashdot.org/story/11/11/11/2036245/linux-kernel-power-bug-is-fixed](http://linux.slashdot.org/story/11/11/11/2036245/linux-kernel-power-bug-is-fixed)

Anyone know where I can download the Ubuntu kernel with this patch applied to test it? I have a feeling it's not the Sandy Bridge graphics bug fix, but it might help.

---

### Post by sbraz on 2011-11-12
```
sbraz@sbraz-netbook:~$ uname -r
3.1.1-custom
```
it can be done. ;)

---

### Post by crysman on 2011-11-12
> **steevven1 said:**
> Virtually all of your power savings are coming from this kernel parameter: i915.i915_enable_rc6=1

This parameter is known to cause graphical glitches and system freezes  on Sandy Bridge processors, just so you know. Are you experiencing any  problems like this?

On my ThinkPad X220 (also with a Sandy Bridge i7), this kernel parameter  causes HUGE power savings and also graphical glitches and freezes.

I use this parameter as well, I am not experiencing any problems. But I am not using NVIDIA graphic card...

---

### Post by UnsolvedCypher on 2011-11-12
try 
```
sudo top
```
and see what's eating up power. I had this issue. upstart-udev-bridge was eating up mine, so whenever I started up my computer, I would just do 
```
sudo top
``` then press k then type the process' PID and hit enter, then type kill. It worked for me!

---

### Post by Matti L on 2011-11-12
For a long time I thought that my laptop battery was broken because I could only use it for 15 minutes, but then I used Vista after a long time and noticed it could go on for over an hour. Lame.

---

### Post by joneswm on 2011-11-12
Has anyone got a 11.10 build of kernel 3.2 with the new APSM patch that they'd like to share, possibly on BitTorrent?  (preferably x86_64)  I'd rather not go to the effort of building this if someone has already gone through the effort.  Thanks.  William.

---

### Post by Gremlinzzz on 2011-11-12
I was having power problems when i installed Ubuntu 11.10.
Now I'm testing/using Linux Mint 12 'Lisa' RC.
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
heating problems are gone? no problems:popcorn:

---

### Post by Bucic on 2011-11-14
> **joneswm said:**
> has anyone got a 11.10 build of kernel 3.2 with the new apsm patch that they'd like to share, possibly on bittorrent?  (preferably x86_64)  i'd rather not go to the effort of building this if someone has already gone through the effort.  Thanks.  William.
**[size="4"]+1[/size]**

---

### Post by Toz on 2011-11-14
See: [https://wiki.ubuntu.com/Kernel/PowerManagement]("https://wiki.ubuntu.com/Kernel/PowerManagement") with kernels available from: [http://zinc.canonical.com/~cking/powermanagement/mjgaspmfix/oneiric/]("http://zinc.canonical.com/~cking/powermanagement/mjgaspmfix/oneiric/").

---

### Post by sbraz on 2011-11-14
thank you toz, you saved us a lot of troubles.


download the appropriate kernel-image AND kernel-headers lovely couple, move them somewhere safe, then open a terminal, go to that path and issue this:

```
sudo dpkg -i *.deb
```

i'll compile 3.1.1 with [[COLOR="Blue"]_"da patch"_[/COLOR]]("lkml.org/lkml/diff/2011/11/10/467/1") i've just successfully applied to the vanilla sources and test it tomorrow, i left my charger at work... **again**. :(

```
root@sbraz-netbook:/usr/src/linux-3.1.1/source# patch -p1 < ../../kernel-patches/aspm.patch 
patching file drivers/acpi/pci_root.c
patching file drivers/pci/pci-acpi.c
Hunk #1 succeeded at 393 (offset -2 lines).
patching file drivers/pci/pcie/aspm.c
patching file include/linux/pci-aspm.h
```

GO GO GO! :)

---

### Post by ali0chka on 2011-11-14
Anxiously awaiting reports. I just ordered an X220 myself, and cannot envision reverting to W7.

Has anyone tried the solution posted by the guys at Phoronix? They claim the issue is with the APSM controller....and they also claim to have found a workaround (no permanent fix), which might be good for some, for the time being. 

Look [[COLOR="Blue"]here[/COLOR]]("http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1")

---

### Post by ali0chka on 2011-11-14
Just realized it was the solution posted by Toz...

:/

---

### Post by steevven1 on 2011-11-14
Trying to install the patched kernel. I get the following errors:

```
$ sudo dpkg -i *.deb
(Reading database ... 169410 files and directories currently installed.)
Preparing to replace linux-headers-3.0.0-13-generic 3.0.0-13.22+mjgaspmfix (using linux-headers-3.0.0-13-generic_3.0.0-13.22+mjgaspmfix_amd64.deb) ...
Unpacking replacement linux-headers-3.0.0-13-generic ...
Preparing to replace linux-image-3.0.0-13-generic 3.0.0-13.22+mjgaspmfix (using linux-image-3.0.0-13-generic_3.0.0-13.22+mjgaspmfix_amd64.deb) ...
Examining /etc/kernel/preinst.d/
Done.
Unpacking replacement linux-image-3.0.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
Setting up linux-headers-3.0.0-13-generic (3.0.0-13.22+mjgaspmfix) ...
dpkg: dependency problems prevent configuration of linux-image-3.0.0-13-generic:
 linux-image-3.0.0-13-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.0.0-13-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-13-generic

```

Help?

---

### Post by ali0chka on 2011-11-14
Did you try:

> sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade


Be sure to post any error it spits out.

---

### Post by steevven1 on 2011-11-14
Okay, I got it sorted out and tested the new, patched kernel. Turns out my power consumption is 83-92% of the power consumption using sbraz's "nosparseirq" kernel (see post 62 and nearby posts of this thread), which itself was a marginal improvement over the stock kernel that came with Xubuntu.

It DEFINITELY does not fix the problem that this thread is all about though, which is the Sandy Bridge graphics power bug. That bug is much more drastic a power problem (for Sandy Bridge users) than the bug that has been patched.

Anyway, bottom line: It IS worth installing the new, patched kernel. I'm on a ThinkPad X220 with a Intel Sandy Bridge i7 processor, btw.

IDEA: Maybe someone could combine the edits sbraz made with the nosparseirq kernel with the new patch!

---

### Post by ali0chka on 2011-11-14
:(

---

### Post by ali0chka on 2011-11-14
@steeven1

Have you tried any other power management tweaks? I'm just wondering whether one can get the battery life up to somewhat acceptable values while this bug gets fixed. I'm particularly thinking of [this]("http://www.lesswatts.org/tips/") from lesswats.org (which apparently is ran by Intel people) and [this]("http://29a.ch/2011/10/14/review:-ubuntu-linux-on-thinkpad-x1") which works for the Thinkpad X1 (Ignore the TRIM section, seeing you don't use SSD). 

I've been able to juice out 10-15% more battery from previous notebooks using similar methods. Albeit not perfect, I don't like to see people revert to Win just because of battery issues ;)

There is also a lot of great info on people using the X220 and Ubuntu [here]("http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-28.html")

---

### Post by Bucic on 2011-11-15
Patched "3.0.0-13.22+mjgaspmfix" kernel **tested on Lenovo Thinkpad T500. No luck! It didn't work at all. Works same as default install and config.**
> GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 pcie_aspm=force"

Edit:
Simple kernel upgrade/downgrade instructions
[http://ubuntuforums.org/showpost.php?p=11391743&postcount=8](http://ubuntuforums.org/showpost.php?p=11391743&postcount=8)

BTW, after successfull kernel upgrade you should get something like
```

~$ uname -a
... 3.0.0-13-generic #22+mjgaspmfix ...

```

---

### Post by ali0chka on 2011-11-15
Look at post #282 in this forum 

[http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-29.html](http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-29.html)

The user there claims idling at 7.5 to 10W...with screenshots

Running Debian Sid with custom 3.1 kernel.

---

### Post by Bucic on 2011-11-15
That's great but I am no expert. I need a feasible solution.

---

### Post by steevven1 on 2011-11-15
> **ali0chka said:**
> Look at post #282 in this forum 

[http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-29.html](http://forum.notebookreview.com/lenovo-ibm/575569-linux-x220-29.html)

The user there claims idling at 7.5 to 10W...with screenshots

Running Debian Sid with custom 3.1 kernel.

That guy's results are 100% believable, since he is using this kernel parameter (quoted from his post from your link): pcie_aspm=force i915.i915_enable_rc6=1

I've used that parameter and gotten the same results. It uses an older graphics driver which is buggy and causes (infrequent, intermittent) graphical glitches and even complete system freezes. Almost 100% of his power savings is coming from that parameter; I guarantee it.

The glitches and freezes that occur with that parameter can take days to show up, or they can show up instantly. They can be really bad one day and nonexistent the next. He may not have even seen one yet. I tested this extensively for long periods of time myself (on my X220 with the i7).

In response to your previous question: With the new, patched 3.0 kernel, I get 4.3-4.7 hours of ACTUAL (not estimated based on power usage, but experimentally measured over hours....I'll give a better estimate when I have used the patched kernel for a few days or weeks) battery life on the 6-cell battery (versus probably 5.5-7 hours with Windows...I can't give a more precise measurement because I didn't use Windows for long). The laptop is noticeably warmer with Linux than with Windows, too. Those time estimates are with the brightness at about 60%, browsing the Internet and reading documents, doing some heavier things like running a VirtualBox every now and then, but not most of the time.

PLEASE feel free to share this post with the folks at the other thread you linked to. I'd like to know what that guy says...If he is experiencing it too. I have two X220's, and both have shown the same exact results for me.

---

### Post by tushantin on 2011-11-16
I haven't given this a try yet on my HP Mini 210, because...

HP Mini 210
F0.4
32
3.1.0-2-generic
11.3W
3.1.0-2-generic
11.7W

[According to this]("https://wiki.ubuntu.com/Kernel/PowerManagement"), the ASPM power fix actually makes it worse for 32 bit. :(

---

### Post by Cyclane on 2011-11-16
I use a 32 bit install. and added the  pcie_aspm=force to grub and I see a improvement. My laptop went from 22W to 17W. Although I believe my computer doesn't have a sandy bridge design but a Arrandale.

Although I would like to know how people get their power usage down to 10W.

---

### Post by MadPoet on 2011-11-16
I was starting to believe that it was my laptop's problem and that I would need to buy a new battery... I was looking at the patches at the Ubuntu Wiki but I just have no idea which one to download: the one that says linux headers or linux image? Sorry for the n00b question. :oops:

---

### Post by Bucic on 2011-11-16
> **MadPoet said:**
> I was starting to believe that it was my laptop's problem and that I would need to buy a new battery... I was looking at the patches at the Ubuntu Wiki but I just have no idea which one to download: the one that says linux headers or linux image? Sorry for the n00b question. :oops:
[http://ubuntuforums.org/showpost.php?p=11460009&postcount=150](http://ubuntuforums.org/showpost.php?p=11460009&postcount=150)

---

### Post by MadPoet on 2011-11-16
> **Bucic said:**
> [http://ubuntuforums.org/showpost.php?p=11460009&postcount=150](http://ubuntuforums.org/showpost.php?p=11460009&postcount=150)
Thanks. ;) I'll install them tonight, let's see if it'll do the trick. *crosses fingers

---

### Post by steevven1 on 2011-11-23
I heard a rumor that this Sandy Bridge power mess is supposed to be fixed (by Intel) in kernel 3.2, but with no source cited. Anyone know anything about that?

---

### Post by Epinephrin3 on 2011-11-23
> **steevven1 said:**
> I heard a rumor that this Sandy Bridge power mess is supposed to be fixed (by Intel) in kernel 3.2, but with no source cited. Anyone know anything about that?

There's some info over at Phoronix about RC6 being enabled by default in the 3.2 kernel

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTQ)

---

### Post by steevven1 on 2011-11-24
> **Epinephrin3 said:**
> There's some info over at Phoronix about RC6 being enabled by default in the 3.2 kernel

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTQ)


Interesting. I wonder if RC6 is going to be modified too, because for me, turning it on means an unstable system with graphical glitches as of kernel 3.0 (though it does solve the power issue).

---

### Post by ali0chka on 2011-11-25
Ok, I just received my X220 in the mail today, and after tinkering with it for the last 5 hours, I managed to significantly reduce the power consumption to around 6.5W with wifi and bluetooth off by following the guidelines [here]("http://ubuntuforums.org/showthread.php?p=11411115"). With Wifi on it idles around 7.3W. 

I'm running a fresh install of 11.10, downloaded today from the ubuntu website. Unity is disabled, and I'm running gnome classic with cairo dock, compiz and 3D effects on...and that's about it. 

X220 i5-2520M 8gb ram and the X-25M Intel SSD (160gb). Right now battery is at 27% with (predicted) 1h 48min to go. 

Will keep posted about real life usage...I'm falling asleep on my keyboard right now...

---

### Post by ali0chka on 2011-11-27
So, following up on the previous post, and after extended testing, I've been getting around 5h of battery with wifi on, a couple of tabs open on chrome and programming in Python and Matlab (manly text and simple calc). I'm wondering whether the newer BIOS fixed some issues...I honestly don't understand why everyone else is getting such bad battery life...

Also, I'm running a 6 cell battery. Right now, with WLAN on, I'm idling at around 8W

---

### Post by steevven1 on 2011-11-28
Are you using i915?

Also, 8 W on an 70 W*h battery (the six cell) should give 8-9 hours of battery life, but you're reporting only 5. My configuration sucks down about 14-17 W at idle to light browsing (no i915, acpi patched kernel 3.0, no other tweaks) and gets (as I said before) about 4.25 hours of battery life (similar to you). There's no way you're only drawing 8 watts.

If you're using i915, I'd expect you to only draw 8-11 watts and to get 6-9 hours of battery life, but I'd also expect you to experience graphical glitches and freezes occasionally.

No disrespect (thanks for the report), but it just doesn't add up.

---

### Post by ali0chka on 2011-11-30
No disrespect taken! I'm looking forward to having this bug fixed. 

Yes, I'm using the i915...and as of yet I have had one system freeze...but it was me being stupid with python. As far as graphical glitches are concerned, I've had none...

With wlan off, and hardwired I can squeeze over 7 hours (60% brightness, no sound and light browsing/code writing). For some reason my wlan card alone draws ~7W (regardless of load) according to powertop vs 3W from eth0 when I'm jacked in. 

All in all, this is the best battery life I've had in Ubuntu, in relation to windows, in any laptop I have ever had. In my old Dell XPS1340 (which shipped with Ubuntu), and the Vaio before that I was lucky to get half. I know it doesn't address the point that it is a buggy kernel, but in my personal experience with this PC its not all bad ;)

---

### Post by redlinethecar on 2011-11-30
Glad to know it's not just me. I was wondering when switching from windows to linux my battery life dropped significantly.
I have an alienware m17x r3

Here is my output from powertop
```
PowerTOP 1.97     Overview   Idle stats   Frequency stats   Device stats   Tunables                                     

Summary: 0.0 wakeups/second,  0.0 GPU ops/second and 0.0 VFS ops/sec

                Usage       Events/s    Category       Description
            100.0%                      Device         Audio codec alsa:hwC0D3: acer-aspire-7730g (Intel)
            100.0%                      Device         Audio codec alsa:hwC0D0: acer-aspire-7730g (IDT)
              6.8 ms/s       0.0        Process        /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
              5.8 ms/s       0.0        Process        /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wr
              4.3 ms/s       0.0        kWork          disk_events_workfn
              3.5 ms/s       0.0        Process        gnome-terminal
              3.4 ms/s       0.0        Process        /usr/lib/firefox-8.0/plugin-container /var/lib/flashplugin-installer/npwrapper.libflashplayer.so -greomni /usr/lib/firefox-8.0/
              2.2 ms/s       0.0        Interrupt      PS/2 Touchpad / Keyboard / Mouse
              2.1 ms/s       0.0        Process        /usr/lib/firefox-8.0/firefox
              1.7 ms/s       0.0        Timer          hrtimer_wakeup
              1.3 ms/s       0.0        Interrupt      [6] tasklet(softirq)
              0.8 ms/s       0.0        Process        /usr/bin/mono --runtime=v4.0.30319 /usr/bin/jupiter.exe
            631.9 µs/s       0.0        Process        /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
            548.4 µs/s       0.0        Process        powertop
            498.0 µs/s       0.0        Timer          tick_sched_timer
            461.3 µs/s       0.0        Interrupt      [43] iwlagn
            422.1 µs/s       0.0        Interrupt      [42] i915
            360.5 µs/s       0.0        Process        /usr/bin/python /usr/bin/software-center
            313.4 µs/s       0.0        Interrupt      [4] block(softirq)
            307.6 µs/s       0.0        Process        /sbin/wpa_supplicant -u -s -O /var/run/wpa_supplicant
            286.0 µs/s       0.0        Interrupt      [7] sched(softirq)
            181.6 µs/s       0.0        Interrupt      [1] timer(softirq)
            152.8 µs/s       0.0        Interrupt      [9] RCU(softirq)
            137.1 µs/s       0.0        Process        /usr/sbin/irqbalance
            133.5 µs/s       0.0        Process        syndaemon -i 0.5 -K -R
            109.5 µs/s       0.0        Process        dbus-daemon --system --fork --activation=upstart
            106.1 µs/s       0.0        Process        [rtsx-polling]
             88.0 µs/s       0.0        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
             85.1 µs/s       0.0        Interrupt      [41] SATA controller
             78.9 µs/s       0.0        Process        [kworker/u:4]
             74.1 µs/s       0.0        kWork          ieee80211_iface_work
             73.6 µs/s       0.0        Process        gnome-panel
             68.7 µs/s       0.0        Process        //bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
             68.3 µs/s       0.0        Interrupt      [9] acpi
             67.9 µs/s       0.0        Timer          process_timeout
             62.2 µs/s       0.0        Process        /usr/lib/upower/upowerd
             57.8 µs/s       0.0        Process        [flush-8:0]
             57.6 µs/s       0.0        Timer          delayed_work_timer_fn
             51.3 µs/s       0.0        Process        [kworker/u:5]
             36.4 µs/s       0.0        Process        [kworker/0:0]
             35.6 µs/s       0.0        Process        nautilus -n
             34.1 µs/s       0.0        Process        udisks-daemon: polling /dev/sr0 /dev/sdb
             33.1 µs/s       0.0        Process        nm-applet
             32.8 µs/s       0.0        Process        NetworkManager
             30.4 µs/s       0.0        kWork          iwl_bg_run_time_calib_work
             26.6 µs/s       0.0        kWork          vmstat_update
             24.7 µs/s       0.0        Process        update-notifier

```

lspci:
```
sean@sean-M17xR3:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GTX 460M] (rev a1)
07:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
0d:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5e)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

I can't fix this issue for the life of my. I'm stuck programming in windows until i figure this out............

---

### Post by steevven1 on 2011-11-30
> **ali0chka said:**
> 

Yes, I'm using the i915...and as of yet I have had one system freeze...but it was me being stupid with python. As far as graphical glitches are concerned, I've had none...



Glad to hear you're not experiencing the graphical bugs. Maybe the i915 driver is better with the i5 processor. I have two X220's with the i7 processor (2620M), and both give me glitches and freezes with i915 enabled :-(

---

### Post by ali0chka on 2011-12-02
@redlinethecar

Have you tried to go through the mods posted in this thread? Also, what kernel are you running, and what is your hardware. I assume, seeing that it is an alienware, that you have independent graphics, or a independent hybrid. 

If you go through the hacks maybe you will see a better battery life, if not, post your HW specs and maybe we can be of help.

---

### Post by crysman on 2011-12-02
> **steevven1 said:**
> Glad to hear you're not experiencing the graphical bugs. Maybe the i915 driver is better with the i5 processor. I have two X220's with the i7 processor (2620M), and both give me glitches and freezes with i915 enabled :-(

I am not having any graphical problems neither with ```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
``` added in GRUB boot options.

I've experienced some feezes, though. But not many. Running *3.0.0-13-generic #22-Ubuntu SMP* (Xubuntu) on *ASUS U36SD*

---

### Post by steevven1 on 2011-12-02
> **crysman said:**
> I am not having any graphical problems neither with ```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
``` added in GRUB boot options.

I've experienced some feezes, though. But not many. Running *3.0.0-13-generic #22-Ubuntu SMP* (Xubuntu) on *ASUS U36SD*

Am I right in assuming that you also have the i5 processor?

---

### Post by crysman on 2011-12-05
> **steevven1 said:**
> Am I right in assuming that you also have the i5 processor?

Yes, Intel core i5.

---

### Post by cupevampe on 2011-12-05
Hi guys, i also have an i5 laptop, and the temperature the cpu/gpu can reach sometime worry me... today the gpu went to 99 and the cpu to 85... frankly enough to be worried

i use the laptop mainly for work and i really need it, can't afford it to fail on me and want it to last as long as possible.

I've installed both the patched kernel and he grub fix, perhaps the situation is slightly better, as i type this (using Lubuntu though!) temperature is down to 52-55 C... only with Chrome open.

Windows stays at 48-50 even with chrome and torrents... basically i cannot use unity or gnome despite having a perfectly capable machine :(

i was wondering if i could install some older ubuntu to get lower temps and possibly longer battery life... what do you say?

---

### Post by ali0chka on 2011-12-06
That's pretty odd. Have you checked your thinkfan settings? Are you sure it is running? If so, type: 

```
sudo thinkfan -n
``` 

In a terminal and see if it spits any error out. You might have some non-overlapping values, which can cause thinkfan to fail. 

Also, I've experienced my first graphical glitch. Yesterday on youtube, the video started stuttering...I had to log off to solve it. I don't know though if this is flash related, but I would say its more likely, since playing AVI, WMV or MKV I haven't had any issues. Any notes on this anyone?

---

### Post by quarara on 2011-12-06
I have an I3 sandy bridge processor and I experience glitches with rc6 enabled both with 3.1 and 3.0 kernel.

---

### Post by steevven1 on 2011-12-06
> **ali0chka said:**
> 
Also, I've experienced my first graphical glitch. Yesterday on youtube, the video started stuttering...I had to log off to solve it. I don't know though if this is flash related, but I would say its more likely, since playing AVI, WMV or MKV I haven't had any issues. Any notes on this anyone?

Most of my graphical glitches with rc6 enabled were while typing text (in vi, Firefox web fields like gmail, etc). The text would get garbled, and scrolling cleared it up again. I don't think I ever experienced video glitches, but I did see some other stuff occasionally, so it's not impossible.

---

### Post by ali0chka on 2011-12-06
Ohhhh...I see. I actually get that on my desktop on 10.04 with the last few kernel updates (2.X kernels).  However, If i run 2.6.35, its ok...never bothered to post a bug though, since it only happen very so often. How often did this happen to you? ( by you previous posts, I assume enough to be a serious nuisance)

---

### Post by steevven1 on 2011-12-07
> **ali0chka said:**
> Ohhhh...I see. I actually get that on my desktop on 10.04 with the last few kernel updates (2.X kernels).  However, If i run 2.6.35, its ok...never bothered to post a bug though, since it only happen very so often. How often did this happen to you? ( by you previous posts, I assume enough to be a serious nuisance)

It was a serious nuisance. It would happen so often sometimes that I couldn't get any programming done, but then sometimes the problem would leave me alone for a whole day (or happen only once or twice in a day)!

---

### Post by Bucic on 2011-12-14
Quick question. My laptop keeps heating up my house even though it's a C2D system (not sandy bridge, I don't know the arch. name for C2D). Should I pursue the same solutions as Sandy Bridge users? I mean apart from the rc grub line - the patched kernels, kernel downgrades, aspm force...

---

### Post by bryanchicken on 2011-12-14
anyone had a chance to try the Pangolin alpha with the 3.2 kernel to see if it fixes this issue? I think i read somewhere (might have been this thread) that it was planned for fix in 3.2?
It really is a terrible bug as far as i'm concerned. I've even considered returning to windows because of it.

---

### Post by Bucic on 2011-12-14
[**[SIZE="3"]Phoronix - ASPM Kernel Power Fix Won't Land Until Linux 3.3[/SIZE]**]("http://www.phoronix.com/scan.php?page=news_item&px=MTAyMjk")

Ubuntu wiki still contains info on some joint effort [https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement)

---

### Post by bryanchicken on 2011-12-14
thanks Bucic.
I do love linux (traditionally a windoze user but i made the switch) but this is really disappointing. 
Despite making the switch i'm not one of those people that can be bothered compiling kernels and what-not, and i'm sure i'm not the only one. 
Sandybridge hardware, i imagine, must be pretty commonplace what with it being the current Intel hardware. Thats a lot of people that this must be affecting, whether they've noticed or not.
I've no idea when the 3.3 kernel is due out but i think 12.04 should be put back until then. 
Pangolin is a LTS release too. There will be people installing it and forgetting about it for years. Think how many extra watts of power that will be costing the earth!

When they say canonical will be patching for Pangolin. Do they mean it will be fixed in the 3.2 kernel supplied out of the box or do they mean they will be providing a fix for the user to sort out? The former is acceptable i guess

---

### Post by Bucic on 2011-12-15
I have no idea, sorry. Please refer to the queskion at Askubuntu.com
[**What is a realistic date for the kernel power regressions fixes?**]("http://askubuntu.com/questions/72121/what-is-a-realistic-date-for-the-kernel-power-regressions-fixes")

Unfortunatelly it will be a long time before it gets fixed plus until then we'll have to deal with douches like this one [http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html](http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html)

---

### Post by bryanchicken on 2011-12-16
Wow, that is an angry guy!
I particularly like this bit:
"The remaining complaints Michael blindly points at the kernel are most likely configuration problems in the Ubuntu distribution itself (Unity or other application maybe), in the Xorg video driver stack shipping with Ubuntu, or operator error."

I can't pretend to understand all this stuff but i was running Ubuntu mini with no X running. The only package i installed above the mini distribution packages was openssh-server.
I still had massive power draw, so i highly doubt its Unity.

I actually did the i965 rc_6 grub command line fix mentioned earlier in the thread and it worked. Not experienced any glitches yet.

---

### Post by Bucic on 2011-12-16
> **bryanchicken said:**
> Wow, that is an angry guy!
I particularly like this bit:
"The remaining complaints Michael blindly points at the kernel are most likely configuration problems in the Ubuntu distribution itself (Unity or other application maybe), in the Xorg video driver stack shipping with Ubuntu, or operator error."

I can't pretend to understand all this stuff but i was running Ubuntu mini with no X running. The only package i installed above the mini distribution packages was openssh-server.
I still had massive power draw, so i highly doubt its Unity.

I actually did the i965 rc_6 grub command line fix mentioned earlier in the thread and it worked. Not experienced any glitches yet.
You're making a mistake of even trying to discuss with his... assessments. The bug has been confirmed on launchpad.net by ubuntu devs plus there's a dedicated ubu wiki page for this particular issue and there some sorry #%@ specialist pop up like the issue itself wasn't PITA enough. It's not worth discussing here.

---

### Post by fuduntu on 2011-12-18
> **Bucic said:**
> You're making a mistake of even trying to discuss with his... assessments. The bug has been confirmed on launchpad.net by ubuntu devs plus there's a dedicated ubu wiki page for this particular issue and there some sorry #%@ specialist pop up like the issue itself wasn't PITA enough. It's not worth discussing here.

So, I'm the guy that wrote the article and I have more experience with the issue than you can ever pretend to comprehend.  You can discount it all you want, but I have proven the regression false on multiple occasions.

For example:

A **T420** with the "regression" - **7 watts**. - [http://www.fuduntu.org/forum/viewtopic.php?f=13&t=1282](http://www.fuduntu.org/forum/viewtopic.php?f=13&t=1282)

An **ASUS U56E** Laptop with the "regression" - **7 watts** - [http://www.fuduntu.org/forum/viewtopic.php?f=13&t=1520](http://www.fuduntu.org/forum/viewtopic.php?f=13&t=1520)

The bug has been confirmed by people that don't comprehend the basics of configuration and testing, it is not a kernel problem it is a configuration problem.  Is there room for power optimization in the kernel? Sure.  Is there a regression? No.

If you look at the following data set with the claimed fix - you will find that the "fix" really didn't amount to much except in the case of a small number of machines - as I implied.

[https://wiki.ubuntu.com/Kernel/PowerManagementASPM](https://wiki.ubuntu.com/Kernel/PowerManagementASPM)

Check out the **T420** thinkpads with the "fix", **14.89W - 9.14W - 19.54W**, see the pattern?  They are all using too much power because they are all configured wrong. If **I can make them use 7 watts with a simple configuration change**.  Hmm..

The test procedure isn't valid either, they should reboot the computer before testing for the baseline, and test with no apps running.  Then do the same with the new kernel.  They don't do that though, so there is no telling what was running before and what is running after.

There is also no collection of data used to gather the metrics so it can't be analyzed, meaning unfortunately that it is all invalid.  Amateur test cases at best.

My ASUS (linked above) with the regression is currently sitting at **38 degrees Celsius**, with Chromium, Thunderbird, Pidgin and a bunch of other apps running while connected to AC power.

I can see now how it is a kernel problem though, thanks for pointing it out, genius.

---

### Post by fuduntu on 2011-12-18
> **bryanchicken said:**
> Wow, that is an angry guy!
I particularly like this bit:
"The remaining complaints Michael blindly points at the kernel are most likely configuration problems in the Ubuntu distribution itself (Unity or other application maybe), in the Xorg video driver stack shipping with Ubuntu, or operator error."

I can't pretend to understand all this stuff but i was running Ubuntu mini with no X running. The only package i installed above the mini distribution packages was openssh-server.
I still had massive power draw, so i highly doubt its Unity.

I actually did the i965 rc_6 grub command line fix mentioned earlier in the thread and it worked. Not experienced any glitches yet.

Angry because idiots flood the internets with stupid crap like Phoronix which leads users that aren't knowledgeable enough to  know better to believe their doom and gloom sky is falling stories to be true.

---

### Post by Bucic on 2011-12-18
**fuduntu**
you may be right - we're not knowledgeable enough. That's why you should bring your findings up on launchpad, get devs attention and let us know how it went.

Second - are there some instructions written by you on dealing with the misconfigurations you claim are the cause for? Edit: I mean instructions that apply to a wider range of configurations (i.e. C2D platforms, not Sandy Bridge) and that are comprehensible by noobs?

---

### Post by fuduntu on 2011-12-18
> **Bucic said:**
> **fuduntu**
you may be right - we're not knowledgeable enough. That's why you should bring your findings up on launchpad, get devs attention and let us know how it went.

Second - are there some instructions written by you on dealing with the misconfigurations you claim are the cause for?

If you read any of the articles or posts that I wrote, including the one you linked, you would have found instructions in every single one of them.

You may not be, but I am knowledgeable enough, so you should watch who you call names because sometimes that person knows far more than you do about the situation.

If anyone at Ubuntu / Launchpad wants to learn how to properly test this, they all know where to find me.  I don't have an account at Launchpad, nor do I have any interest in creating one.  I have enough work to do at Fuduntu.

---

### Post by tushantin on 2011-12-18
**Fuduntu**, your methods require the use of your distro, but unfortunately as I'm an end-user artist (not a programmer) it may be a while till I give it a serious try. However...

I'm using HP Mini 210, 32 bit, and [according to the "latest fix"]("https://wiki.ubuntu.com/Kernel/PowerManagementASPM"), kernel 3.1 would still give me 11.7w of power consumption. I'm not even using Sandy Bridge, and that's still quite high. 

How would you suggest to get it down to 8 or 7 watts?

---

### Post by Bucic on 2011-12-18
> **fuduntu said:**
> If you read any of the articles or posts that I wrote, including the one you linked, you would have found instructions in every single one of them.

You may not be, but I am knowledgeable enough, so you should watch who you call names because sometimes that person knows far more than you do about the situation.

If anyone at Ubuntu / Launchpad wants to learn how to properly test this, they all know where to find me.  I don't have an account at Launchpad, nor do I have any interest in creating one.  I have enough work to do at Fuduntu.
I'm asking because I see nothing special e.g. in that topic about T420. Just the usual grub line fixes everyone who faces the, let's call it **excessive heating**, has been juggling around with little success. On top of that you add installation of thinkfan. The last one seems obsolete to me as my fan runs at max (3000 RPM) all the time and it's unable to keep the CPU below 50 deg C. I hope now you understand my hesitation.

---

### Post by fuduntu on 2011-12-18
> **tushantin said:**
> **Fuduntu**, your methods require the use of your distro, but unfortunately as I'm an end-user artist (not a programmer) it may be a while till I give it a serious try. However...

I'm using HP Mini 210, 32 bit, and [according to the "latest fix"]("https://wiki.ubuntu.com/Kernel/PowerManagementASPM"), kernel 3.1 would still give me 11.7w of power consumption. I'm not even using Sandy Bridge, and that's still quite high. 

How would you suggest to get it down to 8 or 7 watts?

The methods are generic and can be applied to any distro.  There are lots of threads in this very forum that discuss using most of these tuning parameters / software.  Jupiter is available for Ubuntu from webupd8.

My distribution just improves some of the defaults.

---

### Post by fuduntu on 2011-12-18
> **Bucic said:**
> I'm asking because I see nothing special e.g. in that topic about T420. Just the usual grub line fixes everyone who faces the, let's call it **excessive heating**, has been juggling around with little success. On top of that you add installation of thinkfan. The last one seems obsolete to me as my fan runs at max (3000 RPM) all the time and it's unable to keep the CPU below 50 deg C. I hope now you understand my hesitation.

The topic rolls up all of the commonly applied parameters, and adds thinkfan (to the t420).

Your CPU fan wouldn't run at max all the time if something wasn't causing it to run at max.  Look at your process table, after applying the tweaks and you still see a problem you'll most likely find it there.

Note that I am using kernel 3.1.4 also.  Your comment really seems to indicate that it is probably something specific to Ubuntu.

---

### Post by Bucic on 2011-12-18
> **fuduntu said:**
> The topic rolls up all of the commonly applied parameters, and adds thinkfan (to the t420).

Your CPU fan wouldn't run at max all the time if something wasn't causing it to run at max.  Look at your process table, after applying the tweaks and you still see a problem you'll most likely find it there.
You have to understand that I wasted _tens of hours_ trying those "fixes" and even older kernels with no luck. Before I get back into this crap I need to be tossed a detail that would convince me about the slightest REAL chance of success.

As for the processes. I haven't seen anything over 30% the entire time of my testing, ever. I used the System Monitor as well as the **htop**.

Again - I don't use Snady Bridge platform. I use C2D laptop (T500).

---

### Post by fuduntu on 2011-12-18
> **Bucic said:**
> You have to understand that I wasted _tens of hours_ trying those "fixes" and even older kernels with no luck. Before I get back into this crap I need to be tossed a detail that would convince me about the slightest REAL chance of success.

As for the processes. I haven't seen anything over 30% the entire time of my testing, ever. I used the System Monitor as well as the **htop**.

Again - I don't use Snady Bridge platform. I use C2D laptop (T500).

C2D, I have one also (T400), it idles between 7-8 watts.  Perhaps you should try those tweaks with Fuduntu or another Linux distro and see if the problem disappears.

I test this stuff on a variety of machines, I don't just make it all up. ;)

---

### Post by tushantin on 2011-12-18
[QUOTE=Fuduntu]Next, remove /etc/X11/xorg.conf.[/QUOTE]

I'm quite skeptical about doing that in Oneiric / Natty...

EDIT: To be fair, I *am* using Jupiter. Still not the results I'm expecting.

---

### Post by Bucic on 2011-12-18
> **fuduntu said:**
> C2D, I have one also (T400), it idles between 7-8 watts.  Perhaps you should try those tweaks with Fuduntu or another Linux distro and see if the problem disappears.

I test this stuff on a variety of machines, I don't just make it all up. ;)
It may sound strange but I'd like to stay with Ubuntu. All in all I won't dig into it unless your findings are confirmed by other sources or unless you personally do a case with T500. Until then I'll rest with my heater...

The distro thing:
I recall users of other distros reporting the same problems so another 'no, thank you.' Second - you could prove in 30 minutes that it's Ubuntu's fault by taking that 8W T420, installing Ubuntu (default) and applying your fixes that worked under Fuduntu.

One last thing:
ISO's and kernels are ridiculously easy to test so if you have a source of the 3.1.4 kernel or an ISO you think is worth a try (Ubuntu only, Fuduntu maybe...), please post the links.

P.S. If this whole thing comes up in the future to be like you told it all was, I'll publicly apologize. Then I'd like to know who DA #$ was responsible for all that mess because the world has the right to know the name of those #$^% saboteurs (I don't take idiocy into account).

EDIT:
Regarding the 
> Next, remove /etc/X11/xorg.conf.
Are you sure it's not part of the official ubuntu guide on installing AMD drivers? Are you sure user needs to do it even using the official automatic AMD Catalyst installer?

EDIT:
BTW, after I gave up I left my GRUB parameters like this
```
GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 radeon.modeset=0"
```

---

### Post by fuduntu on 2011-12-18
> **Bucic said:**
> It may sound strange but I'd like to stay with Ubuntu. All in all I won't dig into it unless your findings are confirmed by other sources or unless you personally do a case with T500. Until then I'll rest with my heater...

A T500 isn't much different than a T400, the biggest difference is the screen size.  Of course there are models with differing hardware, but if you would like to send me your T500 I'll fix it for you.  I'm not that expensive, personalized service runs about $250/hour US if interested.

> **Bucic said:**
> 
The distro thing:
I recall users of other distros reporting the same problems so another 'no, thank you.' Second - you could prove in 30 minutes that it's Ubuntu's fault by taking that 8W T420, installing Ubuntu (default) and applying your fixes that worked under Fuduntu.

I spent years working on power management on Ubuntu only to find the platform to be buggier than anything.  Users of other distros are reporting great success with Jupiter + the other tweaks mentioned.  It's all over google. ;)

The fact that I am using kernel 3.1.4 on a T420 and not having a problem with the "regression" simply proves that it is a configuration problem and not a kernel problem.

> **Bucic said:**
> 
One last thing:
ISO's and kernels are ridiculously easy to test so if you have a source of the 3.1.4 kernel or an ISO you think is worth a try (Ubuntu only, Fuduntu maybe...), please post the links.

The source to the kernel I use is in my source repo, you are welcome to pull it down and build it.

> **Bucic said:**
> 
P.S. If this whole thing comes up in the future to be like you told it all was, I'll publicly apologize. Then I'd like to know who DA #$ was responsible for all that mess because the world has the right to know the name of those #$^% saboteurs (I don't take idiocy into account).

It's already been proven, several times.  In this thread and others in this forum.  If you want to believe Phoronix, go ahead.  Michael makes a lot of money from his doomsday scenarios.

There is a sucker born every minute, which is what keeps Phoronix in business.

> **Bucic said:**
> 
EDIT:
Regarding the 

Are you sure it's not part of the official ubuntu guide on installing AMD drivers? Are you sure user needs to do it even using the official automatic AMD Catalyst installer?

Xorg will automatically configure itself, the removal of the xorg.conf is for an issue with a specific version of xorg, you probably don't need to worry with it.

> **Bucic said:**
> 
EDIT:
BTW, after I gave up I left my GRUB parameters like this
```
GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 radeon.modeset=0"
```

Did you also install Jupiter, and the latest version of the ATI drivers from ATI?  You should look into it if you haven't.

---

### Post by tushantin on 2011-12-19
Fuduntu, living in the third world country,  $250/hour would take *months* of my salary in a single hour. 

Just curious, though. Why won't you contribute this configuration fix to the parent branch of Ubuntu? That way, wouldn't everyone benefit from it?

P.S.: I'll try the grub parameter soon, though I have Jupiter and it doesn't give me the desired result yet. Not even close.

---

### Post by fuduntu on 2011-12-19
> **tushantin said:**
> Fuduntu, living in the third world country,  $250/hour would take *months* of my salary in a single hour. 

Just curious, though. Why won't you contribute this configuration fix to the parent branch of Ubuntu? That way, wouldn't everyone benefit from it?

P.S.: I'll try the grub parameter soon, though I have Jupiter and it doesn't give me the desired result yet. Not even close.

Sorry to hear it is too expensive for you.  Perhaps Bucic can swing it though to get his T500 supported since he did specifically ask for me to go out of my way to test on a T500.

I'll be happy to oblige if he would be willing to ship the T500, and pay my hourly rate.

Ubuntu isn't my upstream, and I have no desire to go to them with fixes, as historically they have cared more for shine over function.

---

### Post by Bucic on 2011-12-19
Fuduntu,

You misunderstood me. I said that I need to see a T500 case to even start to think about spending another hours on further troubleshooting. Nothing more. BTW, saying that core iX platform is so similar*** to C2D platform is silly.

***enough to follow the same troubleshooting procedures.

I use AMD cat 11.10 and kernel version 3.0.*14* I have tried kernels v 2.6.32 and 2.6.34 with no luck. That alone would prove you right... 3.1.4 and 3.2.*rc* both give me laggy graphics but there's too much crap going on in Unity and compiz (multiple concurrent bugs, sweet) to blame it on kernels.

I really really wouldn't like to switch to non-ubuntu distro but I downloaded Fuduntu and Fedora 16 yesterday. With an external hdd it will be a breeze to test them out without losing my current ubuntu install.

On the Fuduntu's decision not to commit fixes to ubuntu. First and foremost if there's crap in ubuntu it's the multiple dev team corporation that should get on it - not some free soul. Simple as that.

What's the most worrying is that apparently (apparently) ubuntu lead devs are so off the real problems in the distro, that guy who supposedly have the fixes, chooses to create his own fork rather than trying to, I imagine, hit the wall of ubuntu team.

---

### Post by fuduntu on 2011-12-19
> **Bucic said:**
> Fuduntu,

You misunderstood me. I said that I need to see a T500 case to even start to think about spending another hours on further troubleshooting. Nothing more. 

What you actually said was - "unless you personally do a case with T500".  I will be happy to do this for you if you would ship me your T500, and pay my hourly rate.

> **Bucic said:**
> BTW, saying that core iX platform is so similar*** to C2D platform is silly.

```
$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping    : 10
cpu MHz        : 2534.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips    : 5053.94
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping    : 10
cpu MHz        : 2534.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips    : 5053.73
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
$ sudo dmidecode -s system-version
ThinkPad T400

```You were saying?  Go back and read post #194 again. ;)


> **Bucic said:**
> I use AMD cat 11.10 and kernel version 3.0.*14* I have tried kernels v 2.6.32 and 2.6.34 with no luck. That alone would prove you right... 3.1.4 and 3.2.*rc* both give me laggy graphics but there's too much crap going on in Unity and compiz (multiple concurrent bugs, sweet) to blame it on kernels.

You may have a problem with airflow.

> **Bucic said:**
> I really really wouldn't like to switch to non-ubuntu distro but I downloaded Fuduntu and Fedora 16 yesterday. With an external hdd it will be a breeze to test them out without losing my current ubuntu install.

It's worth trying.  You wouldn't even need to install to test.  Just boot the live image and unplug.

> **Bucic said:**
> On the Fuduntu's decision not to commit fixes to ubuntu. First and foremost if there's crap in ubuntu it's the multiple dev team corporation that should get on it - not some free soul. Simple as that.

I tried for a few years to help out, I abandoned Ubuntu a long time ago and have been much better off since.  They are talking about including my software (Jupiter) in the next version of Ubuntu, but of course the last I read about it they are considering ripping out the core functionality and then abandoning the upstream project.  So - they will have a fork that over time no longer works right, just like everything else they fork.

> **Bucic said:**
> What's the most worrying is that apparently (apparently) ubuntu lead devs are so off the real problems in the distro, that guy who supposedly have the fixes, chooses to create his own fork rather than trying to, I imagine, hit the wall of ubuntu team.

Fuduntu is not a fork of Ubuntu, the name is just for the fun of it.

---

### Post by Bucic on 2011-12-19
> **fuduntu said:**
> 
What you actually said was - "unless you personally do a case with T500".  I will be happy to do this for you if you would ship me your T500, and pay my hourly rate.

Let's drop it. I didn't mean any paid services and that's that.
 > **fuduntu said:**
>  
You were saying?  Go back and read post #194 again. ;) 
  
I missed that one, sorry.

 > **fuduntu said:**
>  
You may have a problem with airflow.
  
That doesn't occur on windows? :)

 > **fuduntu said:**
>  It's worth trying.  You wouldn't even need to install to test.  Just boot the live image and unplug. 
  
I have bad experiences with 'hey, just test the live cd!'. See my Sig.


 > **fuduntu said:**
>  
Fuduntu is not a fork of Ubuntu, the name is just for the fun of it.
I stand corrected. The general thought remains the same. You preferred to go your own way.

---

### Post by fuduntu on 2011-12-19
> **Bucic said:**
> Let's drop it. I didn't mean any paid services and that's that.

Ok, fair enough.
  
> **Bucic said:**
>  I missed that one, sorry.

;)

  
> **Bucic said:**
>  That doesn't occur on windows? :)

Well then no, it must be something in Ubuntu somewhere.  I didn't realise it was ok in Windows.

> **Bucic said:**
> I have bad experiences with 'hey, just test the live cd!'. See my Sig.

Fair enough, but the Fuduntu live image is typically what the OS install looks like, minus updates.  It is built from a kickstart and not cobbled together from someone's install turned live cd with revisor.

> **Bucic said:**
> I stand corrected. The general thought remains the same. You preferred to go your own way.

I did, and this year has been the most stable I've seen yet for a Linux desktop for that reason.

---

### Post by Bucic on 2011-12-19
I'll give it a try in the less than 5 hours from now. The sensors terminal command will be enough to see if it did the trick.

---

### Post by fuduntu on 2011-12-19
> **Bucic said:**
> I'll give it a try in the less than 5 hours from now. The sensors terminal command will be enough to see if it did the trick.

Mouse over the Jupiter icon, it will tell you the temp.

You can also -
beesu yum install powertop
beesu powertop

Which will install a version of powertop compatible with the newer kernel.  You won't get the i915 kernel options by default, but you can add them when you boot the live image to get the full effect.

---

### Post by Bucic on 2011-12-19
I'm not sure if we should continue here or in another topic. I'll stick to this topic as there's no any other real help being provided anywhere.

So, I've fired up Fuduntu live cd. My first thoughts:
[LIST=1]
[*]Fuduntu default livecd session doesn't seem to perform any better than my current configured Ubuntu install (configured= aspm force and installed AMD catalyst, nothing more)
[*]I'm not sure anymore windows 7 provided low temperatures and virtually inaudible fan operation on my Thinkpad, after all this. I could swear it did but I will check it sooner or later. Any tips on data collection in case I restore my Win 7 disk image, apart from CPUID Hardware Monitor?
[/LIST]

Fuduntu-14.12-x86_64-LiveDVD.iso - default session
Lenovo Thinkpad T500
AMD HD 3650
SSD OCZ Agility 3
BIOS settings - all defaults, except:
* Intel AMT disabled
* power settings: battery optimized / ballanced where applicable

Screenshots:
first shots - cable plugged in, perf mode, t=55 deg C
later screenshots - battery unplugged, performance mode, t=55 deg C
LATER - battery unplugged, power saving mode, t=45 deg C

fan at 3000+ RPM in every case

Screenshots: [http://www.mediafire.com/?k2aumgr2gz3pi7u](http://www.mediafire.com/?k2aumgr2gz3pi7u)

---

### Post by fuduntu on 2011-12-19
> **Bucic said:**
> I'm not sure if we should continue here or in another topic. I'll stick to this topic as there's no any other real help being provided anywhere.

So, I've fired up Fuduntu live cd. My first thoughts:
[LIST=1]
[*]Fuduntu default livecd session doesn't seem to perform any better than my current configured Ubuntu install (configured= aspm force and installed AMD catalyst, nothing more)
[*]I'm not sure anymore windows 7 provided low temperatures and virtually inaudible fan operation on my Thinkpad, after all this. I could swear it did but I will check it sooner or later. Any tips on data collection in case I restore my Win 7 disk image, apart from CPUID Hardware Monitor?
[/LIST]

Fuduntu-14.12-x86_64-LiveDVD.iso - default session
Lenovo Thinkpad T500
AMD HD 3650
SSD OCZ Agility 3
BIOS settings - all defaults, except:
* Intel AMT disabled
* power settings: battery optimized / ballanced where applicable

Screenshots:
first shots - cable plugged in, perf mode, t=55 deg C
later screenshots - battery unplugged, performance mode, t=55 deg C
LATER - battery unplugged, power saving mode, t=45 deg C

fan at 3000+ RPM in every case

Screenshots: [http://www.mediafire.com/?k2aumgr2gz3pi7u](http://www.mediafire.com/?k2aumgr2gz3pi7u)

Temps look good, looks like you just need to install and configure thinkfan and you'll be good to go.

---

### Post by Bucic on 2011-12-20
> **fuduntu said:**
> Temps look good, looks like you just need to install and configure thinkfan and you'll be good to go.
How am I good to go when Fuduntu gives me same as Ubuntu which is nowhere near what windows 7 provides. I'be just installed windows 7 again. Temp is 40 and fan runs slower. See the pattern? If I slow down the fan to windows speed on linux I'll get higher temps. No brainer.

---

### Post by fuduntu on 2011-12-20
> **Bucic said:**
> How am I good to go when Fuduntu gives me same as Ubuntu which is nowhere near what windows 7 provides. I'be just installed windows 7 again. Temp is 40 and fan runs slower. See the pattern? If I slow down the fan to windows speed on linux I'll get higher temps. No brainer.

That isn't necessarily true.  Keep in mind I have a T400 and a T420.  Using thinkfan, my fan slowed down significantly and my temps didn't rise.  The fan in the machine is just brain dead, a typical IBM / Lenovo problem.

---

### Post by Bucic on 2011-12-20
> **fuduntu said:**
> That isn't necessarily true.  Keep in mind I have a T400 and a T420.  Using thinkfan, my fan slowed down significantly and my temps didn't rise.  The fan in the machine is just brain dead, a typical IBM / Lenovo problem.
I think you missed that bit
> **Bucic said:**
> ...Fuduntu gives me (edit: nearly) same as Ubuntu which is nowhere near what windows 7 provides.
You also add that my fan may slow down without temp increase. Well, taking the following into account:
1. The radiator near outlet was burning hot on linux.
2. Basic thermodynamics.
...your claim is impossible. While you may be an expert in computer science, I'd like to keep to my knowledge of thermodynamics.

Conclusion: Another failed trial.

To make the case even more clear - results of a quick test on Windows 7 SP1:
power saving mode: temp 42 deg C, **FAN INAUDIBLE** (so I quickly switched to other mode not to kill someone involved with linux development)
balanced mode/performance mode: temp 46 deg C, fan very quiet (probably at ~2000 RPM out of 3000 possible; I didn't find any indicators that would include fan RPM)
[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/speedfan_win7_power.png[/IMG]
[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/batterybar_windows7_power.png[/IMG]

---

### Post by fuduntu on 2011-12-20
> **Bucic said:**
> I think you missed that bit

You also add that my fan may slow down without temp increase. Well, taking the following into account:
1. The radiator near outlet was burning hot on linux.
2. Basic thermodynamics.
...your claim is impossible. While you may be an expert in computer science, I'd like to keep to my knowledge of thermodynamics.

Conclusion: Another failed trial.

To make the case even more clear - results of a quick test on Windows 7 SP1:
power saving mode: temp 42 deg C, **FAN INAUDIBLE** (so I quickly switched to other mode not to kill someone involved with linux development)
balanced mode/performance mode: temp 46 deg C, fan very quiet (probably at ~2000 RPM out of 3000 possible)
[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/speedfan_win7_power.png[/IMG]
[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/batterybar_windows7_power.png[/IMG]

Ok, sounds like you should be using Windows.  I'm not sure why you would be trying to use Linux since you obviously can't seem to make it work properly.

I don't see how it could possibly be "burning hot" if it's sitting between 45 and 55 degrees Celsius, and in Windows it's only 1 degree cooler (per your screenshot) but ok. :D

---

### Post by Bucic on 2011-12-20
continued...

**Interesting observation re operating temperature and BIOS:**
I exited windows at 45 deg C and quickly entered BIOS settings. That very moment I heard the fan spinning up like crazy, to the full speed I got so borred listening to while using linux. The case part near the cooler outlet up to that moment pretty cool got heated up in no time. Is it a normal behavior?


One more thing about you being right and everything I've read including official channels wrong:
You can go to [https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement) then to [https://wiki.ubuntu.com/Kernel/PowerManagementASPM](https://wiki.ubuntu.com/Kernel/PowerManagementASPM) -> [https://lkml.org/lkml/2011/11/10/467](https://lkml.org/lkml/2011/11/10/467) (a patch by Matthew Garrett). The bloke seems to be a coder that works directly on linux kernel... addressing the problem you claim does not exist... publishing his patches on the Linux Kernel Mailing List. Now, a simple man I am, let's make it simple. Since the Fuduntu quick test wasn't any revelation please show me an official linux kernel dev team member bashing the 'non-existent power PROBLEMS*' and I'll become your follower, giving fuduntu some humble donation. Without it I don't see a reason to discuss this any further.

*
since many so called specialists obviously lost contact with reality which is **Linux turns broad range of computers into house heaters**.
I avoided the term 'regression' on purpose. Because I don't have the patience to see a single more lawyer sentence about naming conventions.

> **fuduntu said:**
> Ok, sounds like you should be using Windows.  I'm not sure why you would be trying to use Linux since you obviously can't seem to make it work properly.
That's where 'lost contact with reality' fits perfectly again. It's not a freakin' Gentoo! I'm talking about ubuntu here. If you intended Fuduntu to be a DIY system than you should have said so on the main web page. "End user should not be forced to fiddle with system guts to make system just barely usable". Repeating that bored users long time ago as anything it has brought is specialists proof to that fundamental.
> **fuduntu said:**
> 
I don't see how it could possibly be "burning hot" if it's sitting between 45 and 55 degrees Celsius, and in Windows it's only 1 degree cooler (per your screenshot) but ok. :D
That's why I told you I'd rather stick with my thermodynamics knowledge.
hints: temp sensor location, fan RPM
'Burning' was en exaggeration though.

---

### Post by fuduntu on 2011-12-20
> **Bucic said:**
> continued...

**Interesting observation re operating temperature and BIOS:**
I exited windows at 45 deg C and quickly entered BIOS settings. That very moment I heard the fan spinning up like crazy, to the full speed I got so borred listening to while using linux. The case part near the cooler outlet up to that moment pretty cool got heated up in no time. Is it a normal behavior?

Do you remember what I said about the fan controller being brain dead?  Thanks for confirming.

> **Bucic said:**
> 
One more thing about you being right and everything I've read including official channels wrong:
You can go to [https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement) then to [https://wiki.ubuntu.com/Kernel/PowerManagementASPM](https://wiki.ubuntu.com/Kernel/PowerManagementASPM) -> [https://lkml.org/lkml/2011/11/10/467](https://lkml.org/lkml/2011/11/10/467) (a patch by Matthew Garrett). The bloke seems to be a coder that works directly on linux kernel... addressing the problem you claim does not exist... publishing his patches on the Linux Kernel Mailing List. Now, a simple man I am, let's make it simple. Since the Fuduntu quick test wasn't any revelation please show me an official linux kernel dev team member bashing the 'non-existent power PROBLEMS*' and I'll become your follower, giving fuduntu some humble donation. Without it I don't see a reason to discuss this any further.


The patch by Mr. Garrett is an optimization of the previous patch by Mr. Garrett that I discussed in my article that you obviously didn't read.  As I've already indicated in this thread, those links aren't properly testing the "fix".  You'll also note that only a few show improvements.

I don't care if you want to be my "follower" or not.  I have enough history improving battery life of users in this very forum that your opinion doesn't carry any weight.

> **Bucic said:**
> 
*
since many so called specialists obviously lost contact with reality which is **Linux turns broad range of computers into house heaters**.
I avoided the term 'regression' on purpose. Because I don't have the patience to see a single more lawyer sentence about naming conventions.

:rollseyes:


> **Bucic said:**
> 
That's where 'lost contact with reality' fits perfectly again. It's not a freakin' Gentoo! I'm talking about ubuntu here. If you intended Fuduntu to be a DIY system than you should have said so on the main web page. "End user should not be forced to fiddle with system guts to make system just barely usable". Repeating that bored users long time ago as anything it has brought is specialists proof to that fundamental.

That is a problem inherent to Linux, as it is not a consumer ready platform.

> **Bucic said:**
>  That's why I told you I'd rather stick with my thermodynamics knowledge.
hints: temp sensor location, fan RPM
'Burning' was en exaggeration though.

Obviously, 45 vs 44 degrees is serious business. :guitar:

---

### Post by Bucic on 2011-12-20
> **fuduntu said:**
> Do you remember what I said about the fan controller being brain dead?  Thanks for confirming.
Do you remember me reporting inaudible fan on windows?

> **fuduntu said:**
> 
The patch by Mr. Garrett is an optimization of the previous patch by Mr. Garrett that I discussed in my article that you obviously didn't read.

I don't recall your article mentioning Mr. Garrett outraged by the 'Phoronix stories'.

> **fuduntu said:**
> 
You'll also note that only a few show improvements.
Me included. No improvements afer trying the "patched kernel" *3.0.0-13-generic-pae_3.0.0-13.22+mjgaspmfix*

> **fuduntu said:**
> 
I don't care if you want to be my "follower" or not.  I have enough history improving battery life of users in this very forum that your opinion doesn't carry any weight.
It's not about that. It's about me being ready to acknowledge you being right as soon as I get some legitimate confirmation. Right now it settled at 'your word vs theirs'. You have to understand as it's thanks to you from now on I won't trust even major website owners ;)


About linux turning PCs into heaters:
It's a fact we both agree on. You just like to add 'because of poor configuration' while I, as vast majority of Ubuntu users, don't care about the reason.

> That is a problem inherent to Linux, as it is not a consumer ready platform.
The most refreshing statement I've read this year. Perhaps if others would have been able to admit it they could have focus more on making it consumer ready rather than 'making it more candy' and 'up to date with the recent technology'.


> **fuduntu said:**
> 
Obviously, 45 vs 44 degrees is serious business. :guitar:
windows:45 deg C at 2000 fan RPM
linux:45 deg C at 3100 fan RPM
I told you to leave thermo to me.
BTW, Fuduntu reported 55 deg C but it was a clean install without the grub line tricks or any other tweaks alterations.

Funny thing. As I write this my temps dropped to 49/47, 2988 fan RPM (instead of my usual ~3088). I was testing the crappy compiz/unity combination recently. The latest of unusual things I did include:
- booting with kernel v 3.1.0-030100-generic instead of the usual 3.0.*14* from here [http://zinc.canonical.com/~cking/powermanagement/mjgaspmfix/oneiric/](http://zinc.canonical.com/~cking/powermanagement/mjgaspmfix/oneiric/) ; where did I get that 3.1.0-030100, I have no idea
- running on battery alone, no cable
- running powertop, then quit
- running thinkfan, both as regular user and sudo, then quit
- removing nomodest (radeon.modeset=0) from my grub cfg which has been GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm="force" i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 [COLOR="Silver"]radeon.modeset=0[/COLOR]" for a month now
* I've noticed screen dimming again. I haven't seen it for a while either.

**~$ ps -A** returns no process with "top" or "fan" in process name but
```
~$ cat /proc/acpi/ibm/fan
status:		enabled
speed:		3020
level:		auto

```


WTH has just happened?! 5 minutes after the unusual temps drop I plugged in the cable, and noticed the fan immediately spinning down. **It span down to 2016 RPM!!!** I did the same later with the same result.
```
~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +48.0°C  (crit = +127.0°C)
temp2:        +46.0°C  (crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        2016 RPM
```

While writing this post in Opera browser with 10 tabs opened it settled at 51/48/3014. powertop launched without computer restart shows discharche rate of circa 25-26 W compared to Win 7 high performance mode discharge rate of 21.2 W.
Edit: Test done after restart (Linux): 45/44 3008 23 W @ 65% backlight

---

### Post by steevven1 on 2011-12-21
Guys,

Respectfully, this is not relevant to the topic of this thread. When I check back here, I'd like to be able to see if there is any news about the Sandy Bridge power problems in the kernel quickly, without sifting through pages of arguments about fans.

Please try PM or a new thread.

Thanks.

---

### Post by Bucic on 2011-12-21
> **steevven1 said:**
> Guys,

Respectfully, this is not relevant to the topic of this thread. When I check back here, I'd like to be able to see if there is any news about the Sandy Bridge power problems in the kernel quickly, without sifting through pages of arguments about fans.

Please try PM or a new thread.

Thanks.
You're right, sorry. But anyone suffering from the issue, please give the 3.1.0-030100-generic kernel along with the grub line parameters from **post #214** a try and report back. 

On the other hand [http://askubuntu.com/questions/84348/is-the-power-regression-overheating-bug-fixed-in-kernel-3-2](http://askubuntu.com/questions/84348/is-the-power-regression-overheating-bug-fixed-in-kernel-3-2)

---

### Post by fuduntu on 2011-12-21
> **steevven1 said:**
> Guys,

Respectfully, this is not relevant to the topic of this thread. When I check back here, I'd like to be able to see if there is any news about the Sandy Bridge power problems in the kernel quickly, without sifting through pages of arguments about fans.

Please try PM or a new thread.

Thanks.

All of my comments have been power related and apply to Sandy Bridge laptops including the comments about fans as they use gobs of power when running.

---

### Post by tushantin on 2011-12-23
Not sure if you guys know this, but...
[http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=3](http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=3)

> Under graphics load the ASPM regression causes the Core i7 notebook to be burning through six more Watts (an increase of 14%) than when ASPM is active. When trying out today's ASPM patch, the power is back to the levels experienced on Linux 2.6.37. Hell yes!

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxNDM](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNDM)

---

### Post by tushantin on 2011-12-24
Tried some of the fixes on HP mini 210. Can't seem to get it below 14w...

---

### Post by Z06Gal on 2011-12-24
I downgraded to the 2.6.39.3 kernel.  It runs totally normal with very little fan use although jupiter seems to help too.  The 3.0 kernel runs about 15 degrees warmer and the fan never goes off.  Hopefully the Precise Penguin kernel will be much better and I plan to hang with the kernel I am running now till then. :)

---

### Post by steevven1 on 2012-01-03
Looks like Linux 3.2 will offer no help for those of us experiencing glitches/freezes when enabling RC6: [http://www.phoronix.com/scan.php?page=news_item&px=MTAzNDg](http://www.phoronix.com/scan.php?page=news_item&px=MTAzNDg)

Crossing my fingers that this will all be over when 3.3 is released....

---

### Post by steevven1 on 2012-01-13
This bug has been marked as "fix released" without any good explanation. Can anyone answer the questions raised in comment #31 here?: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)

---

### Post by steevven1 on 2012-01-13
I have tested kernel 3.2.1 (from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2.1-precise/") ) on my ThinkPad X220, and it seems to use a tad MORE power than kernel 3.0. Ugh.

---

### Post by fuduntu on 2012-01-13
> **steevven1 said:**
> I have tested kernel 3.2.1 (from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2.1-precise/") ) on my ThinkPad X220, and it seems to use a tad MORE power than kernel 3.0. Ugh.

Perhaps Phoronix is wrong.. ;)

---

### Post by steevven1 on 2012-02-15
There is finally, supposedly a patch for this bug! It needs testing!

I have installed the 64-bit kernel from [http://people.canonical.com/~ogasawara/eugeni/rc6/]("http://people.canonical.com/%7Eogasawara/eugeni/rc6/") on my ThinkPad X220 and added the kernel parameter "i915.i915_enable_rc6=1"  (RC6 was off by default). Power consumption was decreased by 25-50%,  extremely roughly. I will test it for several days and then report on  whether I experience glitches or freezes, as I always previously have  with RC6 enabled. Fingers crossed! Thanks for your help and  contributions, everyone.

---

### Post by bryanchicken on 2012-02-16
thanks steevven1.

This is probably a silly question, but i've never upgraded a kernel before:
can i just download and install the .deb and install using dpkg as usual? Does it matter what version (eg, natty/oneiric) of ubuntu i am running?

Do i have to apply that patch somehow or is it built into those .deb files?

Thanks

---

### Post by steevven1 on 2012-02-17
I have tested the patched kernel for about 24 hours now, and it is working beautifully! My battery lasts almost 50% longer (6 hours vs 4.2 hours) than with RC6 disabled, and there are NO glitches or freezes so far!!! Here's how to test it yourself. These instructions presume 64-bit Ubuntu or Xubuntu. For 32-bit, you'll need to DL the 32-bit packages and change the commands accordingly:

1) Download the three files located here to your Desktop:
[http://people.canonical.com/~ogasawara/eugeni/rc6/amd64/]("http://people.canonical.com/%7Eogasawara/eugeni/rc6/amd64/")

2) Run this command:

cd ~/Desktop;sudo dpkg -i linux-headers-3.2.5-tunerc6v1_3.2.5-tunerc6v1_all.deb linux-headers-3.2.5-tunerc6v1-generic_3.2.5-tunerc6v1_amd64.deb linux-image-3.2.5-tunerc6v1-generic_3.2.5-tunerc6v1_amd64.deb
 
3) As root, edit /etc/default/grub such that the line
GRUB_CMDLINE_LINUX_DEFAULT reads like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"

4) Run this command:

sudo update-grub

5) Reboot

6) Never install any kernel updates through Update Manager. They will
replace this patched kernel, which is bad. I recommend uninstalling
all other kernels through your package manager to make sure they don't
try to update, and manually check when you run Update Manager that
nothing beginning with "linux-" is being installed.


You can tell if you did it right by
running this command:

dmesg|fgrep -i "rc6"

after a fresh reboot. The last line of the output should say "enabling
RC6." Also, run:

uname -r

The output of that should tell you that you're running kernel 3.2.5-tunerc6.

Enjoy!

---

### Post by fuduntu on 2012-02-17
> **steevven1 said:**
> I have tested the patched kernel for about 24 hours now, and it is working beautifully! My battery lasts almost 50% longer (6 hours vs 4.2 hours) than with RC6 disabled, and there are NO glitches or freezes so far!!! Here's how to test it yourself. These instructions presume 64-bit Ubuntu or Xubuntu. For 32-bit, you'll need to DL the 32-bit packages and change the commands accordingly:

1) Download the three files located here to your Desktop:
[http://people.canonical.com/~ogasawara/eugeni/rc6/amd64/]("http://people.canonical.com/%7Eogasawara/eugeni/rc6/amd64/")

2) Run this command:

cd ~/Desktop;sudo dpkg -i linux-headers-3.2.5-tunerc6v1_3.2.5-tunerc6v1_all.deb linux-headers-3.2.5-tunerc6v1-generic_3.2.5-tunerc6v1_amd64.deb linux-image-3.2.5-tunerc6v1-generic_3.2.5-tunerc6v1_amd64.deb
 
3) As root, edit /etc/default/grub such that the line
GRUB_CMDLINE_LINUX_DEFAULT reads like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"

4) Run this command:

sudo update-grub

5) Reboot

6) Never install any kernel updates through Update Manager. They will
replace this patched kernel, which is bad. I recommend uninstalling
all other kernels through your package manager to make sure they don't
try to update, and manually check when you run Update Manager that
nothing beginning with "linux-" is being installed.


You can tell if you did it right by
running this command:

dmesg|fgrep -i "rc6"

after a fresh reboot. The last line of the output should say "enabling
RC6." Also, run:

uname -r

The output of that should tell you that you're running kernel 3.2.5-tunerc6.

Enjoy!

Why do you need to install a new kernel?  Just enable the following options in grub:

```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```

---

### Post by bryanchicken on 2012-02-17
fuduntu - just enabling those gives graphical glitches usually. If you aren't getting any then you are lucky.
The glitches for me are particularly annoying during video playback.

steevven1 - thanks for the guide. You're a star. I'll be trying this at the weekend if i get a chance.

---

### Post by hamdori on 2012-02-18
Thanks for detailed instruction. I am also seeing dramatic improvement of battery life. I don't have any number but i can tell you it works. 

> **steevven1 said:**
> I have tested the patched kernel for about 24 hours now, and it is working beautifully! My battery lasts almost 50% longer (6 hours vs 4.2 hours) than with RC6 disabled, and there are NO glitches or freezes so far!!! Here's how to test it yourself. These instructions presume 64-bit Ubuntu or Xubuntu. For 32-bit, you'll need to DL the 32-bit packages and change the commands accordingly:

1) Download the three files located here to your Desktop:
[http://people.canonical.com/~ogasawara/eugeni/rc6/amd64/]("http://people.canonical.com/%7Eogasawara/eugeni/rc6/amd64/")

2) Run this command:

cd ~/Desktop;sudo dpkg -i linux-headers-3.2.5-tunerc6v1_3.2.5-tunerc6v1_all.deb linux-headers-3.2.5-tunerc6v1-generic_3.2.5-tunerc6v1_amd64.deb linux-image-3.2.5-tunerc6v1-generic_3.2.5-tunerc6v1_amd64.deb
 
3) As root, edit /etc/default/grub such that the line
GRUB_CMDLINE_LINUX_DEFAULT reads like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"

4) Run this command:

sudo update-grub

5) Reboot

6) Never install any kernel updates through Update Manager. They will
replace this patched kernel, which is bad. I recommend uninstalling
all other kernels through your package manager to make sure they don't
try to update, and manually check when you run Update Manager that
nothing beginning with "linux-" is being installed.


You can tell if you did it right by
running this command:

dmesg|fgrep -i "rc6"

after a fresh reboot. The last line of the output should say "enabling
RC6." Also, run:

uname -r

The output of that should tell you that you're running kernel 3.2.5-tunerc6.

Enjoy!

---

### Post by steevven1 on 2012-02-18
FROM THE WRITER OF THE PATCH...PLEASE HELP HER OUT:

"
                        Hi Everyone,
 I see some of you have found the RC6 tunables test kernel I built.   As a follow on to that I've been in touch with upstream and have pulled  in a proposed patch which disables RC6p (deep RC6) for Sandy Bridge.   Upstream claims that RC6p is what was responsible for the reports of  hangs/graphics corruption issues when RC6 was enabled.  I've then added a  follow on patch to then enable plain RC6 by default for Sandy Bridge  users.    Both of these patches are available in the latest 3.2.0-17.26  kernel.
 In order to help justify keeping these patches applied and providing  Sandy Bridge users improved power savings by default (ie users will no  longer need to pass in i915.i915_enable_rc6=1), I'd really  appreciate if you could all review my call for testing which I posted to  both the Ubuntu kernel-team and ubuntu-devel mailing lists:
 [https://lists.ubuntu.com/archives/kernel-team/2012-February/019029.html](https://lists.ubuntu.com/archives/kernel-team/2012-February/019029.html)
 If you could please test and provide your feedback on the PowerManagementRC6 wiki, I would greatly appreciate it.
 [https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)
 Thanks in advance."

---

### Post by steevven1 on 2012-02-23
Potentially bad news: I started experiencing freezes again on my X220 with RC6 enabled and the new (tunable RC6) kernel. The freezes only occur (so far) while using LibreOffice Calc, but they are exactly the same types of freezes I have experienced with RC6 before. I have not yet seen the graphical glitches appear as they used to, so that's good news at least. I can't be 100% sure these freezes are related to RC6 and not to LibreOffice Calc, so I'll keep testing, but I suspect that they may be linked to RC6 since I never had a problem with Calc before. I will report back. I would recommend that anyone testing RC6 should use their computer extensively for several days before reporting anything.

---

### Post by fmou on 2012-03-18
I've got the same problem with LibreOffice Calc.
Disabling Hardware acceleration and anti-aliasing in Tools/options/Libreoffice/view fixes the problem.

---

### Post by Bromden on 2012-03-18
```
sudo gedit /etc/default/grub

  Search for this line:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

  Replace the above line with this one and save the file:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"

  Update the Grub by using this command:
  sudo update-grub


```
I found this possible solution on maketecheasier.com
Does it work, or the battery power consumption is still a problem to solve?

---

### Post by steevven1 on 2012-03-21
> **Bromden said:**
> ```
sudo gedit /etc/default/grub

  Search for this line:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

  Replace the above line with this one and save the file:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"

  Update the Grub by using this command:
  sudo update-grub


```I found this possible solution on maketecheasier.com
Does it work, or the battery power consumption is still a problem to solve?


That is the solution to an entirely different problem.

---

### Post by steevven1 on 2012-03-21
The Sandy Bridge power issue is solved, and the patch is applied to the Ubuntu 12.04 (Precise) kernel, and RC6 is enabled by default with this kernel, so no kernel parameters are required, etc.

As for the LibreOffice issue, it seems unrelated to the power issues. There is a bug report for that here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/940771](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/940771)

Marking this thread as SOLVED!

:-D

---

### Post by danls on 2012-03-22
> **steevven1 said:**
> That is the solution to an entirely different problem.

Can you explain this please?  From my reading, setting the boot parameter "pcie_aspm=force" effectively does the same thing (although not as permanently) as the kernel patch, right?

EDIT: oops, i am confusing the RC6 patch for the ASPM patch, my bad!

---

### Post by cendo on 2012-05-25
Hoi, 

so what kind of power consuption should I see for my t420s, i7 2640M?

Currently I see around 25W after implementing the "GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 pcie_aspm=force acpi=noirq quiet splash" "

But the thinkpad last only 1.5hours on battery:( however my fan issue is still not resolved.

thanks
peter

> **steevven1 said:**
> The Sandy Bridge power issue is solved, and the patch is applied to the Ubuntu 12.04 (Precise) kernel, and RC6 is enabled by default with this kernel, so no kernel parameters are required, etc.

As for the LibreOffice issue, it seems unrelated to the power issues. There is a bug report for that here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/940771](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/940771)

Marking this thread as SOLVED!

:-D

---

