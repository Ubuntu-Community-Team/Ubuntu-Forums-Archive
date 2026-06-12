---
title: "Memory leak specific to Swap?"
date: 2012-07-12
forum: General Help
---

### Post by DorianX on 2012-07-12
Hi all,

I recently upgraded my way from Maverick to Precise, which has been a clusterfrak in a lot of ways, but I've managed to tune the thing into a fair approximation of as usable as it was before. Except for one thing.

My swap seems to be leaking. Running the same set of apps (modulo the difference between gnome-classic and gnome 2) as I was running under Maverick, I'm seeing that the "used" amount of swap slowly increases over time, even if the computer is left idle. After about a week, it reaches close to 100% usage, and the system will freeze for a few seconds when switching between applications. Killing my applications (I have not tried logging out and back in) has no effect, and physical memory isn't filling up (Well, Chromium leaks memory like a sieve, but if I kill it a few times an hour, that memory usage goes away). 

I've looked at the output of top, but I'm not really sure how to interpret it; nothing seems out-of-line, not more than on other systems that don't have this problem (The top few programs as listed by swap all showed a value of about 300m in the swap column. I'm not sure what to make of this, since the total swap usage at the time was only 100m). In Maverick, I rarely saw any of my swap get used unless I was completely out of physical memory, but now, I'll see "free -m" report, say, 290m of used swap.

I added up the amount of swap listed in /proc/<pid>/smaps, and it adds up to only a fraction of the amount listed by free -m.

So I'm not really sure how to make sense of these numbers: smaps gives the smallest number, free -m gives a larger number, and top gives a larger number still. But there seems to be no question that my swap *is* filling up, and when it gets completely full, even with lots of free physical memory, the system becomes unresponsive. 

If I try it when the used swap is still fairly modest, only a few hundred megs, I can temporarily fix the problem by doing "swapoff -a; swapon -a".  The swap used resets to zero, physical memory usage does _not_ increase (Seems to me like if you turn off the swap, and there was stuff in there you actually needed, you'd have to move that data into physical memory).  But I tried it the other day when it was using about 2.5 gb out of 3, and the system just became utterly unresponsive. Can't say if it would have come back on its own, as after ten minutes, I reached for the magic sysrq reboot key.

I've tried killing various processes to no avail. I'm pretty much out of techniques to investigate and troubleshoot this further and am looking for ideas.

One thing that I'm suspicious about, and I';ve got no idea how to test it, is that I heard somewhere it was possible for linux to cache data from nfs-mounted shares in the local swap, and this would be pretty bad if true (my local hard disk is slowish and very busy with the other stuff the computer is doing. My network is fast and the remote hard drive is fast).

So, has anyone seen something like this happening? What should I look at to try to circle in on the cause of the problem?

Thanks.

---

### Post by Redblade20XX on 2012-07-13
> **DorianX said:**
> Hi all,

I recently upgraded my way from Maverick to Precise, which has been a clusterfrak in a lot of ways, but I've managed to tune the thing into a fair approximation of as usable as it was before. Except for one thing.

My swap seems to be leaking. Running the same set of apps (modulo the difference between gnome-classic and gnome 2) as I was running under Maverick, I'm seeing that the "used" amount of swap slowly increases over time, even if the computer is left idle. After about a week, it reaches close to 100% usage, and the system will freeze for a few seconds when switching between applications. Killing my applications (I have not tried logging out and back in) has no effect, and physical memory isn't filling up (Well, Chromium leaks memory like a sieve, but if I kill it a few times an hour, that memory usage goes away). 

I've looked at the output of top, but I'm not really sure how to interpret it; nothing seems out-of-line, not more than on other systems that don't have this problem (The top few programs as listed by swap all showed a value of about 300m in the swap column. I'm not sure what to make of this, since the total swap usage at the time was only 100m). In Maverick, I rarely saw any of my swap get used unless I was completely out of physical memory, but now, I'll see "free -m" report, say, 290m of used swap.

I added up the amount of swap listed in /proc/<pid>/smaps, and it adds up to only a fraction of the amount listed by free -m.

So I'm not really sure how to make sense of these numbers: smaps gives the smallest number, free -m gives a larger number, and top gives a larger number still. But there seems to be no question that my swap *is* filling up, and when it gets completely full, even with lots of free physical memory, the system becomes unresponsive. 

If I try it when the used swap is still fairly modest, only a few hundred megs, I can temporarily fix the problem by doing "swapoff -a; swapon -a".  The swap used resets to zero, physical memory usage does _not_ increase (Seems to me like if you turn off the swap, and there was stuff in there you actually needed, you'd have to move that data into physical memory).  But I tried it the other day when it was using about 2.5 gb out of 3, and the system just became utterly unresponsive. Can't say if it would have come back on its own, as after ten minutes, I reached for the magic sysrq reboot key.

I've tried killing various processes to no avail. I'm pretty much out of techniques to investigate and troubleshoot this further and am looking for ideas.

One thing that I'm suspicious about, and I';ve got no idea how to test it, is that I heard somewhere it was possible for linux to cache data from nfs-mounted shares in the local swap, and this would be pretty bad if true (my local hard disk is slowish and very busy with the other stuff the computer is doing. My network is fast and the remote hard drive is fast).

So, has anyone seen something like this happening? What should I look at to try to circle in on the cause of the problem?

Thanks.

I had a problem like that once. It was a renegade os program that got it's configuration file messed up due to an update. Maybe that's what happened in your case and a clean install will fix it.

- Red

---

### Post by Rsjc741 on 2012-07-13
Out of curriosity, what are your system specs?
 
If you have a decent amount of memory, you could probably get away with not using a swap parition.
 
 
If you have 6+ GB of RAM, you can bypass it on the installation.
 
You save space and could possibly have a better running system =)
 
 
Of course, this is if you are going to format your computer anyways.
 
As for your memory leak.. you could always run a debugger or use a task manager to see high-usage applications and from there reinstall the program or try and reformat your computer.

---

### Post by matt_symes on 2012-07-13
Hi 

Check the kernel threads using htop.  (Press the K -uppercase K- key).

Anything with crazy memory useage ?

Kind regards

---

### Post by DorianX on 2012-07-13
Thanks for the ideas. I noticed a weird sluggishness even with lots of free memory last night when switching desktops or invoking the task switcher, and that's leading me to suspect Compiz is the culprit. I'd been using a version of compiz from the compiz-proposed ppa. I switched over to the latest compiz out of main and my swap usage dropped down to something reasonable. Unfortunately, the latest compiz out of main still has the show-stopping bug that sent me to the proposed version in the first place.

For now, I've fallen back to metacity (Which isn't a great permanent solution for me because I have a weird spacial relations issue that makes it hard for me to use multiple workspaces without a smooth transition between them, but I'll live). THe swap use has remained stable over the past few hours, and I'll continue to monitor it. 

I'm still a bit befuddled by the way the swap use for individual programs is tracked though, since smaps and top didn't show compiz or xorg using nearly as much swap as was getting used

---

### Post by matt_symes on 2012-07-13
Hi

What was the show stopping bug ?

Kind regards

---

### Post by d4m1r on 2012-07-13
x2, specs of the machine? If you have 6GB of RAM or more, you should disable swap all together so this would be a non-issue.

---

### Post by DorianX on 2012-07-13
> **matt_symes said:**
> Hi

What was the show stopping bug ?

Kind regards

Whenever I try to switch between workspaces, the screen flashes several times, and any apps that I was dragging to another workspace suddenly snap back to workspace 1

---

### Post by DorianX on 2012-07-13
> **d4m1r said:**
> x2, specs of the machine? If you have 6GB of RAM or more, you should disable swap all together so this would be a non-issue.

Unfortunately, I've only got 2 GB, and it's a notebook, so upgrade paths are limited. I actually could probably make do without any swap about 2/3 of the time, but google reader and twitter are both painfully slow in firefox, so I rely on chromium for a few things (From a browser-experience standpoint, I prefer chromium over firefox by a lot, but the last few months or so, its memory usage has gotten out of hand.)

---

