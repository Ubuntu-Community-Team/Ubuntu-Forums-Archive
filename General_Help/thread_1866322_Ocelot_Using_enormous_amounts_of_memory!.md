---
title: "Ocelot Using enormous amounts of memory!"
date: 2011-10-21
forum: General Help
---

### Post by Turbo556 on 2011-10-21
Hey all this is getting really annoying....

As you can see from the picture below ....my system is using alot of memory....yet I cannot find out where or how.....it says I am using close to 3 gb of ram with my VM running which takes up 600 mb.....but it makes no sense cause when I look at the processes that are using memory they don't add up to anywhere NEAR 3 GB....

Yet when the memory starts getting close to my 4GB Limit my PC starts running very slow......and has crashed before.....

How in the heck do I fix this?

---

### Post by Turbo556 on 2011-10-21
Even with most everything shut down including firefox and thunderbird (though not my VM which uses 600 mb ram) the system says I am using a whoppping 2GB of ram!

---

### Post by Perryg on 2011-10-21
I am seeing this as well.  A clean boot starts out at approx. 600MB and as the day goes on will creep up to 2GB of memory used (not cache but real memory).

After checking it appears that when you use a program it loads the memory but when you close it the memory stays but is marked as asleep.  

It looks almost like (shudder) Windows superfetch.

---

### Post by jim_deadlock on 2011-10-21
Using all RAM is quite normal and it's not necessarily a bad thing, there are many background system processes that all need a bit of memory. What slows the computer down is when it starts using the swapfile because then it has to keep fetching stuff from the hard disk.

A VM will use as much memory as you give it (in the settings for the VM). You are basically running two systems on one computer, so 3G is pretty marginal and you are likely to run out of RAM and overflow into swap.

---

### Post by Perryg on 2011-10-21
I was not running a VM myself. I noticed this with various apps like the CD burning software, nautilus, and various built in apps.  The "top" list continues to grow while using.  Another thing that I have seen in the new release is that logging off and back in seems to clear this issue and starts over rebuilding the memory again.  Plus I must humbly disagree that using all the system RAM is normal.  I have never seen this unless you are actually talking about cache, which is not what I am referring to.

---

### Post by Gatemaze on 2011-10-21
> **jim_deadlock said:**
> Using all RAM is quite normal and it's not necessarily a bad thing, there are many background system processes that all need a bit of memory. What slows the computer down is when it starts using the swapfile because then it has to keep fetching stuff from the hard disk.

A VM will use as much memory as you give it (in the settings for the VM). You are basically running two systems on one computer, so 3G is pretty marginal and you are likely to run out of RAM and overflow into swap.

Depends whether RAM is actively used or it is used as cache...

---

### Post by Gatemaze on 2011-10-21
> **Turbo556 said:**
> Hey all this is getting really annoying....

As you can see from the picture below ....my system is using alot of memory....yet I cannot find out where or how.....it says I am using close to 3 gb of ram with my VM running which takes up 600 mb.....but it makes no sense cause when I look at the processes that are using memory they don't add up to anywhere NEAR 3 GB....

Yet when the memory starts getting close to my 4GB Limit my PC starts running very slow......and has crashed before.....

How in the heck do I fix this?

I don't see any issues with your memory... If you look on the little graph on topright corner then you should be worried only when the dark green goes to the top, at the moment is only half way through... the rest of the memory can be reclaimed as needed and it is used as cache... have you noticed that programs tend to launch faster the second time you launch them in the same session? This is one of the reasons... From the terminal I can see that you have at least 800MB free memory (add the cache). A free -m on my system says that I only have 62MB free :) and of course another 600MB cached.

Are you sure it is memory related the lag on your pc and not a process takes all the computational power?

---

### Post by Mr. Jay on 2011-10-21
With just lightdm running and otherwise only working through ssh, 900 MB of my 16 GB RAM are used, 360 of which are cache. That's already a very high amount for a system state before the start of a desktop environment. My old Debian system would typically be around 200 MB at this point.

But 2.4 GB + 300 MB swap used while running the DE, as in the case of the OP, is definitely far too much.

I just checked *top* with shift-M (sort by memory usage) and the values for allocated physical memory (RES column) don't correctly add up there either. For some processes like X, they are obviously incorrect. Something isn't right about the way this information is presented by the kernel or some library in between.

---

### Post by Turbo556 on 2011-10-21
CONFIRMED: After I rebooted....500mb ram usage with 500 mb in caches......this is a far cry from the 2.5gb it said I was using prior to the reboot....how do you fix this?

---

### Post by Mr. Jay on 2011-10-22
I meant it's the other way around: the memory IS used, but values for the specific processes displayed in the system tools are not correct.

It's normal that you have less memory usage right after booting, because the desktop environment is not loaded yet.

In the Installation & Upgrades forum, I saw that for some people, Unity leaks quite a lot of memory, so there's probably a bug behind this.

---

### Post by Turbo556 on 2011-10-22
Anybody have a fix for this?

---

### Post by Turbo556 on 2011-10-22
Does anyone have a fix for this?

---

### Post by K4NEB on 2011-10-22
i dont think anyone has found a fix for this yet, as i want one too 

its worse than vista!

---

### Post by thatguruguy on 2011-10-22
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Perryg on 2011-10-22
Well I am getting closer to finding out what the cause is.  After the memory has gotten up over 1.6GB I usually log off and back on to regain the lost memory.  I see some zombie programs in the tint2 bottom tab just as it shuts down.  So some program/s is/are not really shutting down it is just being held in limbo and not indicated as still running.

---

### Post by bodhi.zazen on 2011-10-22
> **Perryg said:**
> Well I am getting closer to finding out what the cause is.  After the memory has gotten up over 1.6GB I usually log off and back on to regain the lost memory.  I see some zombie programs in the tint2 bottom tab just as it shuts down.  So some program/s is/are not really shutting down it is just being held in limbo and not indicated as still running.

sounds as if you may have a memory leak.

see if this helps:

[http://www.cyberciti.biz/faq/valgrind-check-for-memory-leaks-in-c-programs/](http://www.cyberciti.biz/faq/valgrind-check-for-memory-leaks-in-c-programs/)

---

### Post by Perryg on 2011-10-22
Thanks bodhi I will of course use this tool as I have in the past.  Right now though I am leaning to zombies.  I am seeing several (up to 7 or 8 ) untitled icons at shutdown only while Ubuntu is purging the programs for log-off. Presently the only leaking program that I can actually verify is compiz. I tested this with an upgrade from 11.04 and a clean install. Both show the same problem.  11.04 does not, so this leads me to believe this is specific issue to 11.10 or maybe a program that is new to 11.10.  Either way I will post my findings.

---

