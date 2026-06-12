---
title: "[SOS] Everything stops (system lags-freezes) when the user is idle"
date: 2009-12-18
forum: General Help
---

### Post by RodGer GR on 2009-12-18
I have a really serious problem which I don't know where it comes from. When I don't move the mouse, everything slows down and stops.
1)The clock stops refreshing
2)The cursor stops blinking
3)Some times video freezes
4)Downloading slows down or even stops
5)Copying files slows down or even stops
6)Some times the wireless network disconnects (connects again when I move the mouse but some times asks again for a password)
7)Screen saver rarely shows up and when it starts stays still without moving as it should.
8 )Animated images (e.g. some forum icons etc) stop moving

*I would be grateful if you could give me a hint on what could cause such a problem. A work around would be nice but I would surely prefer to find what could really cause such a problem.*

Please help :( it is really disturbing and there are many things (e.g. download a large file) I can't do due to this problem. I've also spent so much time configuring my system the way I wanted it and it's such a pity to reinstall.

_Extra info that may help:_
Release: Ubuntu 9.10 (karmic)
GNOME: 2.28.1 (Ubuntu 2009-11-03)
kernel: 2.6.31-16-generic (#53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009)

**_I also use hardy heron on the same computer and there is no such problem_**

Even if you don't have any solution, please ask me for any information, I should provide, that would help to make more clear what causes the problem.

Thanks!

---

### Post by RodGer GR on 2009-12-18
It is so strange :confused:... Even if I choose to log out and stay idle after the little countdown timer shows up, it will practically won't log out as it stops counting after about ten seconds.

---

### Post by RodGer GR on 2009-12-21
Finally I found a work-around. I just added the kernel option nohz=off at the end of the ubuntu 9.10 kernel line in my menu.lst file and now the problems I described earlier disappeared. 

_But_ this is not a real solution. It just disabled dynamic ticks. Disabling dynamic ticks may reduce the battery life. I still wonder if there is any way to fix the problem without disabling dynamic ticks.

Any ideas?

---

### Post by granoff on 2009-12-22
I believe I have the same problem on my 9.10 server. The system, seemingly at random intervals, "lags/freezes" as you put it. Existing network connections are dropped. New network connections cannot be made. The only thing that seems to "wake up" the system is to press return on the console (which is connected via a PS2 KVM switch; no USB here). I note that "pressing return" kicks an interrupt... This system does not run gdm or X, fwiw.

I see this problem in kernels 2.6.31-15 and 2.6.28-16.

I have stopped ntpd, because I thought that was causing the problem. (I had noticed ntpd had exited due to a SEGV one time, which made it the smoking gun.)

I have stopped cupsd, because every time this happens, the last messages on the console concern cups restarting.

I have added clocksource=acpi_pm to my kernel boot options, because the default clocksource, rtc, is reported as unstable.

The "worst" thing I've seen in the logs is a kernel oops in inotify_fsnoticy.c:129, which has been reported a lot, and there is an apparent fix in 2.6.32-rc. (However, some people running that have reported this oops still exists. Moving to 2.6.32-rc is not an option for me.) I've seen these oops' in the log at times at the same time as the "lag/freeze."

Anyway, I am out of smoking guns! This freeze happened just this morning and there is nothing in my logs now at the time it occurred to clue me into what is happening.

I am going to try your "nohz=off" trick and see if that helps me as well. (What does that actually do, anyway?)

Interestingly, I run 9.10 on 2 other systems (a Dell desktop and a Dell laptop) and don't see this issue.

I'll report back if nohz=off has a positive impact for me.

Thanks!

-Mark

---

### Post by RodGer GR on 2009-12-22
> **granoff said:**
> [.....]
I am going to try your "nohz=off" trick and see if that helps me as well. (What does that actually do, anyway?)

Interestingly, I run 9.10 on 2 other systems (a Dell desktop and a Dell laptop) and don't see this issue.

I'll report back if nohz=off has a positive impact for me.

Thanks!

-Mark
It looks like the problem comes from dynamic ticks. 
Dynamic ticks is an patch merged in the Linux kernel (since kernel 2.6.21-rc1) which allows timer ticks only when they are needed. When the user is idle there are no timer interrupts (or.. they are significantly reduced to be more accurate). This results to a slight reduction of power consumption and cpu's temperature. The difference becomes more significant on laptops (battery life), servers(the difference accumulates for systems running 24/7), virtual machines (when you have several Linux instances running the same time).
[Here]("http://lwn.net/Articles/138969/") (link) you can find more info about the patch.

In my case and as it seems your case too, the kernel (2.6.31-16) has a problem with dynamic ticks.
That's why I disabled dynamic ticks adding the _**nohz=off**_ option in the menu.lst file.

I can't reproduce this problem on an other computer so it can be a hardware specific problem. Even on my laptop though (where the problem came up) there was no problem initially and I think that there will be no problem on a clean installation. _It would be useful if we could gather more information concerning under what circumstances this problem shows up. If we find a way to reproduce it we can file a bug and try to fix it._

I found somebody describing a similar problem back when the patch was merged in the 2.6.21 kernel [here (link)]("http://bbs.archlinux.org/viewtopic.php?id=35642"):
> Hi, I've been struggling for some time to get a kernel with dynamic ticks to be stable on my current hardware configuration. Right now, I'm using a Toshiba M40 with a Intel centrino cpu. Basically, what happens is that the system will start slowing down and then completely freeze up after about 5 seconds after the initial slowdown. 

I know this to be an issue with dynamic ticks as disabling it in my kernel build fixed the problem. Disabling HPET timers in the kernel and adding clocksource=acpi_pm as a kernel boot parameter doesn't seem to fix the issue with dynamic ticks. 

So, I'm wondering if others are having this problem (an issue in both 2.6.21 and 2.6.22); and if anyone knows any possible solutions outside of disabling dynamic ticks.

P.S.1: An other 'side effect' of the same problem I didn't mention is that it makes my system clock run slower and finally lose more than an hour per day. Do you have any similar "slow clock" problems?

P.S.2: If anyone reading this has any thoughts that could help us connect the 'dots' and see what may went wrong with dynamic ticks, please, speak freely.

---

### Post by granoff on 2009-12-22
> **RodGer GR said:**
> It looks like the problem comes from dynamic ticks. 
Dynamic ticks is an patch merged in the Linux kernel (since kernel 2.6.21-rc1) which allows timer ticks only when they are needed. When the user is idle there are no **timer interrupts** (or.. they are significantly reduced to be more accurate). ...

Thanks for the explanation.

I think "interrupts" is a clue here (and this is a just a wild theory at this point)... BUT, considering that, at least in my case, when this happens I cannot connect to the machine via the network, *which would require interrupts on the network interface to be working*, then perhaps interrupts is an area to be looked into with respect to dynamic ticks... dunno.

>  This results to a slight reduction of power consumption and cpu's temperature. The difference becomes more significant on laptops (battery life), servers(the difference accumulates for systems running 24/7), virtual machines (when you have several Linux instances running the same time).
[Here]("http://lwn.net/Articles/138969/") (link) you can find more info about the patch.

I am not so much concerned with power consumption or CPU temp, BUT my system is a 24/7 server, fwiw.

> ...
I can't reproduce this problem on an other computer so it can be a hardware specific problem. Even on my laptop though (where the problem came up) there was no problem initially and I think that there will be no problem on a clean installation. _It would be useful if we could gather more information concerning under what circumstances this problem shows up. If we find a way to reproduce it we can file a bug and try to fix it._


Yeah, I can't reproduce it either. And I see nothing in my logs that would suggest any consistent smoking gun. Plus, I can't necessarily say I know enough about the inner workings of the kernel that I know everywhere (other than log files) to look for hints.

> 
P.S.1: An other 'side effect' of the same problem I didn't mention is that it makes my system clock run slower and finally lose more than an hour per day. Do you have any similar "slow clock" problems?

Yup! When I resusitate my system, by pressing enter on the console (which fires an interrupt!), the time on the system is at, or very very close to the time the system froze. I have to reset it using ntpdate. Then everything is A-OK.

> P.S.2: If anyone reading this has any thoughts that could help us connect the 'dots' and see what may went wrong with dynamic ticks, please, speak freely.

Second that! This is a major issue, IMO. Something like handling interrupts (if that is not a red herring) should be a component of the kernel that is rock solid at this point. Anything I can do to help, I am happy to do.

-Mark

---

### Post by RodGer GR on 2009-12-23
Finally, did you try the nohz=off option? What was the result?

---

### Post by granoff on 2009-12-23
> **RodGer GR said:**
> Finally, did you try the nohz=off option? What was the result?

So far so good.

The system has been stable since about 18:00 EDT last night, having booted the 2.6.31-16 kernel with **clocksource=acpi_pm nohz=off**.

BUT, stability over one night doesn't mean anything, at least in my case. I've seen the problem occur after several days of continuous, stable operation.

Interestingly, in a bug report here: 

[http://bugzilla.kernel.org/show_bug.cgi?id=14646](http://bugzilla.kernel.org/show_bug.cgi?id=14646)

where I noted that when I saw the issue reported there along with the issues reported here, the assigned maintainer reported an issue he found with dmesg and sending too much data to the console possibly causing a clock skew.

I referenced this thread, in that thread, in the hopes of gathering more breadcrumbs and getting some more eyes on all this. We'll see what happens.

As and if my system continues to be stable, I will report back.

-Mark

---

### Post by granoff on 2009-12-24
My system remains stable after 1 day and 15+ hours, booted as noted above.

I am not 100% convinced yes, because I've seen the system run for several days before having a problem.

I do, however, have my fingers crossed, because I am going away for a few days and won't be able to fix anything, should anything happen, until the middle of next week when I return. (The good or bad news, depending on how you look at it, is that I'll know well before my return if something happens, because my system will be unreachable. Oh what a feeling of helplessness that will be! :-)

Will continue to report status as necessary.

-Mark

---

### Post by granoff on 2009-12-25
The daily update... :-)

Still up and running, 2 days and 17 hours...

But also still within the window, in my experience with this issue, of "run for a few days and then lag/freeze/etc."

Where I am, at this moment, remote, I am quite pleased that the system is apparently running smoothly!

-Mark

---

### Post by granoff on 2009-12-26
Another day, another update.

Still stable at 3 days 15 hours uptime...

---

### Post by granoff on 2009-12-27
Stable for 4 days 18 hours...

---

### Post by granoff on 2009-12-28
Stable for 5 days 14+ hours...

Past the usual point of failure of "several days", I'd say... I am cautiously optimistic.

---

### Post by granoff on 2009-12-29
Stable for 6 days 15 hours... yay? :-)

---

### Post by granoff on 2009-12-31
I dare say, things are looking good: Stable for 8 days 15 hours and counting...

An idr_callback kernel oops showed up yesterday, I just noticed, but that had no ill effect on the system's stability, as I once thought it was. (And that oops was reported automatically to kernel.org.)

-Mark

---

### Post by oberno on 2010-01-02
I'm having the same issue and I'd like to know how do I edit the menu.lst file. 
I looked for it in /boot/grub/ but there isn't any menu.lst file there

Am I supposed to add nohz=off in the boot menu?(having dual boot with XP). If yes, where exactly am I supposed to add the nohz=off command in there?


Thanks :P

---

### Post by granoff on 2010-01-03
> **oberno said:**
> I'm having the same issue and I'd like to know how do I edit the menu.lst file. 
I looked for it in /boot/grub/ but there isn't any menu.lst file there

Am I supposed to add nohz=off in the boot menu?(having dual boot with XP). If yes, where exactly am I supposed to add the nohz=off command in there?

I am not an expert when it comes to dual booting, but I would imagine you would have access to the boot commands at system startup to choose either Windows or Linux.

So, at that point, you want to edit the 'kernel' line for your Linux boot options and add **nohz=off** at the end.

I do not have a dual boot configuration; just Linux. Here's my default boot options, for an example:

```

title           Ubuntu 9.10, kernel 2.6.31-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-16-generic root=/dev/md4 ro quiet splash quiet clocksource=acpi_pm nohz=off 
initrd          /boot/initrd.img-2.6.31-16-generic

```

At this point, for me, the clocksource=acpi_pm option is probably not doing anything useful, but the system is stable *with* it, so I am leaving it in.

Hope this helps.
-Mark

---

### Post by oberno on 2010-01-03
Thanks a lot for the response :)

However, I used the crontab to enter the ntpd -u command and have it check every X minutes, cause the nohz=off thingy didn't work for me.

---

### Post by JoyousDeath on 2010-01-20
I am also having this problem, though the solution posted here was for grub, I have the grub2 beta so my menu.lst is nonexistent and I'm not sure how to edit the new one.

```

$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

```

Can anyone tell me the workaround until Grub2 is fully released?

---

### Post by JoyousDeath on 2010-01-20
I tried reading over some documentation about Grub2, but it doesn't seem like it'd have a place for nohz=off.

In the old grub I could just add it to the end of the Kernal line, but I'm not sure where it goes in the new grub.

---

### Post by JoyousDeath on 2010-01-20
I tried editing the 40_custom file under /etc/grub.d/ to read simply:

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

nohz=off

```

But restarting right now is not possible since I have critical processes running, will post back a report to see if problem continues.

---

### Post by JoyousDeath on 2010-01-21
I'm back, editing the 40_custom file did not work.

---

### Post by victorinovich on 2010-02-12
;)   [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by webbertiger on 2010-03-10
> **JoyousDeath said:**
> I'm back, editing the 40_custom file did not work.
JoyousDeath,

Try to edit this line in /boot/grub/grub.cfg and reboot:

linux /boot/vmlinuz-2.6.31-20-generic root=UUID=429ed579-3a8f-4654-a7f4-99bf716aaa72 ro   quiet splash **nohz=off**

This works for me.

---

### Post by webbertiger on 2010-03-21
ACPI config also affects this issue. For new grub users, if you have a hyper-threading CPU, you can try to edit /etc/default/grub and use acpi=ht, and you'll see a line like:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi=ht**"

Then run 
**update-grub**

---

