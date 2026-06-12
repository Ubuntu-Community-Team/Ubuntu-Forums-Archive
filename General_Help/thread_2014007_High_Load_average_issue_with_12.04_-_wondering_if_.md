---
title: "High Load average issue with 12.04 - wondering if falling back to 11.10"
date: 2012-07-01
forum: General Help
---

### Post by LeftFoot on 2012-07-01
Hi there,

I just installed 12.04 and I have serious load average spikes.

For exemple with rhythmbox, 10 firefox tab + 2 terminals I can go over 5 or 6 while my CPU idle around 65/70%

So from time to time everything will freeze for 2 to 10 sec.
I use a i7 + 2GB of RAM that should be more than enough to run everything smoothly.

I saw some other ppl complaining about this but didn't find any solution (ppl are talking about an commit kernel issue).

So :
-Is it a know bug of 12.04 ?
-Is it something about my personal conf ?
-Is it anything I can do ? (I am seriously thinking of trying 11.10 )

Thx for any help !

LeftFoot

---

### Post by Doug S on 2012-07-01
There is a reported load averages issue that many have been complaining about.
Under the right conditions, sometimes the reported load average (i.e from "top" or "uptime" commands) can be in errror too high. Apparently, the "right conditions" include Ubuntu desktop editions sitting idle.
 
You also describe an issue with freezing for 2 to 10 seconds, which I know nothing about.
 
By "commit" people are just referring to something called a "Commit-ID" that identifies the patch that was applied to the kernel. Late in the 12.04 release cycle a "commit", or patch, was applied to fix a situation of high actual load averages being reported as 0 load.
 
For the issue of reported load averages, I do not think that going back to 11.10 will help, as that patch has now been backwards applied to many previous kernel verions. However, it might help for your actual freezing issue.
 
Hope this helps:
 
references:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661)
[http://thread.gmane.org/gmane.linux.kernel/1310462](http://thread.gmane.org/gmane.linux.kernel/1310462) 
[http://www.smythies.com/~doug/network/load_average/index.html](http://www.smythies.com/~doug/network/load_average/index.html)

---

### Post by LeftFoot on 2012-07-01
Thx for the info, references and explanation

My system do not exactly freeze : it just become suddenly very very slow : exactly what you can expect with a load average spiking (I saw it go above 8 :( ).

This is definitively not normal. And this is not just top reporting a wrong number. The load average seems really to spike (though how it can when the CPU idle is over 80% eludes me...).

Maybe there is a compatibility issue with my processor and so the kernel doesn't not use all its power ?

Any idea about what I can do on this ?

Thx

LeftFoot

---

### Post by Doug S on 2012-07-01
My test machine has an i7 processor also, and it seems to work fine on 12.04. I have seen other comments about real load issues (vs erroronous reported loads) with 12.04, but never experienced it myself.
 
I agree, you seem to be seeing something real, but just wanted you to be aware of the potential contribution from the eorronous reported part. Are you able to determine, say via "top", what is hogging CPU when you get the spikes?

---

### Post by LeftFoot on 2012-07-01
I don't see any process hogging the CPU.

But for example now : load is > 1 while CPU idle is at 98% !!
This is just not making any sense !

I wonder if I have not 2 issues :

1. the bug reporting the wrong load average (that would explain what I got high load with high idle
2. Something else that hog the CPU from time to time

To make things even more confusing : it seems I didn't get any slow down lately !
I switched from Firefox to Chromium maybe that could explain this ???

Would love to hear about any idea (because I ran out :) )

Thx again !

LeftFoot

---

### Post by rlapa on 2012-07-02
[https://lkml.org/lkml/2012/7/1/19](https://lkml.org/lkml/2012/7/1/19)

---

### Post by LeftFoot on 2012-07-02
not sure if this is related or not.

Surprisingly things improved :
System can be slow for time to time not I don't experience huge slow down anymore.

I switched from VirtualBox to VMware maybe this helped (the link you provided states that VirtualBox might be somehow linked to this)

Top is still reporting big load, but not sure if this is accurate or not.

LeftFoot

---

### Post by osarusan on 2012-07-09
I was wondering if you had any progress on this?

I was the OP over here: [http://ubuntuforums.org/showthread.php?t=2012237](http://ubuntuforums.org/showthread.php?t=2012237) and you thought we had the same problem, but then I said mine was caused by my USB ports... well I was wrong I think, so now I am wondering if maybe we do have the same problem after all.

Did you ever get it fixed?

---

### Post by zwygart on 2012-07-09
May be just give a Idea, load is not only related to CPU usage but also to RAM and disk read/write speed. 

In the first post you talked about 2G of RAM. It should be enough, but at one off my computers I have 3G and I have to pay attention to not fill it (Close unused apps and so on). If the RAM rans over, the computer writes to swap wich is VERY slow. 

May be just also take a look at the RAM usage. To see it in top, start top, press F (upper case), then N to select the sort field to mem and you should see wich application uses the memory. In my case it was often gnome-do and nautilus using up to 50%.

---

### Post by osarusan on 2012-07-10
I have 16 gigs of RAM, and even though I do occasionally use some RAM-heavy programs, the freezes happen even when the PC is idle. Even when nothing but a text editor is open, the blinking cursor will stop and the system will halt for up to 10 seconds or until I move the mouse... so I don't think it's a RAM issue.

---

### Post by LeftFoot on 2012-07-11
> **osarusan said:**
> I was wondering if you had any progress on this?

I was the OP over here: [http://ubuntuforums.org/showthread.php?t=2012237](http://ubuntuforums.org/showthread.php?t=2012237) and you thought we had the same problem, but then I said mine was caused by my USB ports... well I was wrong I think, so now I am wondering if maybe we do have the same problem after all.

Did you ever get it fixed?

Hi Osa,

Agree with you, this is NOT a RAM related issue. I would bet your salary :lol: that this is CPU related.

Myself I received new hardware (SSD drive + 6GB or RAM) and so re-installed everything.

I didn't have too munch time to lay with it yet, but it seems I do not experience freezes anymore (knock on wood , knock on wood !!!).
But I would need to spend some hours to be sure (hopefully I will be able to spend some quality time with my desktop this evening :) ).

I still have a high load though.
Actually this is crazy : My load average is higher on my native Ubuntu Desktop that on my virtualized Ubuntu on my laptop !! :confused:

So I really suspect a hardware compatibility issue.
What kind of hardware do you use ?
Myself I have a Asus P6T motherboard and an 'old' i7 (like 2 or 2 and half year old)

---

### Post by zwygart on 2012-07-12
Ok just throwed an Idea, thanks for the hint, I also had some freezes on my 8G computer (another one). Yes it could be CPU. But I also noticed that the Window Manager may have some influence. What do you think? When I used KDE, Gnome or Unity, all of them freezed some times. But awesome freezes much less time. (And battery lasts longer). On my computer using KDE, CPU usage where normally around 4%, Gnome : 3% and awesome : 1%. (Awesome installed on archLinux and Ubuntu gives the same result.)

If CPU is used, some things use it. But what?

Sorry, inverted Answer and Question :)

---

### Post by LeftFoot on 2012-07-12
> **zwygart said:**
> Ok just throwed an Idea

Sure no worries :)


I do not experience the issue at all :
-no freeze
-load is around 0.78

I have no idea  why is it normal now :-k !!!
But I am not complaining \\:D/

The only difference is :
- I got a brand new hard drive (and Intell SSD that I am starting to love !)
- got 6 GB of RAM instead of 2GB

And actually that might be a RAM / swap / disk issue after all.

I have no swap now and I use 2380MB so just above 2GB.
So if you have 2GB you are swapping and if you have a slow drive / no good driver, this could explain the freeze.
But impossible to know for sure.

Anyway, having more than 2GB looks like a must-have with 12.04  

LeftFoot

---

### Post by zwygart on 2012-07-12
Oh, there we return to the RAM theory? I think that freezes may be due to a lot of things, and not all the freezes posted here related to the same problem. Also the data transfer speed of the RAM and of the drives may have a impact, also the graphical card/pilot and so on. In my case, data transfer to the disks may be the reason for some freezes : When the memory swap over, the CPU usage falls to 3% even if it should be at max with the programms that runs on nice.

---

### Post by osarusan on 2012-07-13
CPU issue? Could be... maybe... but I doubt it.

I've got an AMD Athlon II, which is plenty fast for what I do.

And the weird thing about this skipping -- I regularly work with very heavy loads. Right now I have a bunch of tabs open in Chrome, I'm listening to streaming radio on Audacious, and editing a 1.5 gig file in GIMP. No skips at all. My system is running as smoothly as anything.

But then, later on, when only one or two apps are running -- sometimes only system monitor, sometimes banshee or rhythmbox, or chrome and youtube, then it will skip like crazy.

As long as I keep moving my mouse, the skipping doesn't happen. But if I leave the mouse alone, the skipping happens with 10-20 seconds 100% of the time.

---

### Post by LeftFoot on 2012-07-13
> **osarusan said:**
> CPU issue? Could be... maybe... but I doubt it.

I've got an AMD Athlon II, which is plenty fast for what I do.

I am sure the CPU itself is fine, what I mean is for some reason Ubuntu has trouble managing it.
Having a load > 3 when your CPU idle is 97% just doesn't make any sense.

> As long as I keep moving my mouse, the skipping doesn't happen. But if I leave the mouse alone, the skipping happens with 10-20 seconds 100% of the time.

This is not what I experienced. I just had a slow / unresponsive system with from time to time 5 to 10 sec 'freeze time'.

This had nothing to do with me using my mouse or not.

So this is definitively another issue.

A idea : is it really related to your mouse activity or just your activity. I mean you got spike when you are not touching your mouse but are typing in a windows ?


LeftFoot

---

### Post by zwygart on 2012-07-13
An Idea may be that it is not the CPU nor the RAM, but Xorg (or the graphic card) that has some trouble executing commands from some programs. I noticed slow down in the refresh rate of the screen (about one refresh per several seconds) but the programs and terminals just runned the normal way. 

Some time one tab in Firefox slows down the entire Firefox, but that's another topic. Just give the Idea that a program may not correctly acquire and releases (graphical) ressources.

---

### Post by LeftFoot on 2012-07-13
no I think this is more kernel related than software related. But this is just my opinion so... :D

---

### Post by osarusan on 2012-07-13
It freezes when I type too. One stroke at a time is no problem, but if I hold a key down, it will enter maybe 5-10 characters and then lock up. If I hold backspace, the same happens, it will delete just a few, and then freeze up. If I let the key go and begin typing again, it types fine. Typing individual characters never seems to cause an error -- just holding the keys down.

When I use my PC like I am doing right now -- even just browsing a page or typing, I can see my CPU load drop gradually down. Right now it says 0.71, 1.07, 1.05. But before I replied to this, when the PC was idle, they were all around 1.57.

Maybe it is kernel related? That would make sense I suppose, as this problem happened only within the past few weeks and IIRC there was a kernel update during that time... perhaps best just to wait until the next update?

---

### Post by LeftFoot on 2012-07-14
0.71 is a lot especially if you have a powerfull CPU !

For info a load of 1 mean that your CPU work at 100% !
So 0.7 seems big if you are just browsing and listening to some music.

What is your idle ? (do a 'top'command)

LeftFoot

---

### Post by osarusan on 2012-07-14
Yeah, I thought it was strange too. Interesting, since that last post, I ran pulseaudio -k, and things have been a bit better... I'm still getting high loads, but much much lower than before. Here is my current top:

top - 19:43:50 up  9:15,  0 users,  load average: 0.50, 0.56, 0.56
Tasks: 220 total,   1 running, 218 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.1%us,  3.0%sy,  0.0%ni, 90.9%id,  0.8%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:  16435288k total,  6296932k used, 10138356k free,   528388k buffers
Swap: 16776188k total,        0k used, 16776188k free,  3573612k cached

---

### Post by osarusan on 2012-07-24
Any updates on this? A week has gone by, no patch, no comments... has anyone solved their problem or are you still getting hangs? I still am unable to watch video or play music unless I am constantly moving the mouse to prevent hangs.

---

### Post by HiImTye on 2012-07-25
I'd see how much CPU time the kernel swap daemon is using. check it before and after your system 'hangs'

```
ps -e --format='time comm' | grep kswa
```if it's a memory issue then you'll see the CPU time increase on kswapd0, if it's not then you won't and you'll know it's an errant process.

---

### Post by osarusan on 2012-07-28
Before and after I'm getting 00:00:00

Does this mean its an errant process? Any ideas on how I could isolate which one?

---

