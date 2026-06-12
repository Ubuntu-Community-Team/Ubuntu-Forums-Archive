---
title: "Random freezes in Ubuntu 10.10-- help needed!"
date: 2011-01-15
forum: General Help
---

### Post by sdstolworthy on 2011-01-15
I've been using Ubuntu for a while now, and ever since I installed 10.10 (I did a clean install) I've been having problems with the computer completely locking up... nothing is responsive. I've not had this problem on any prior Ubuntu version. The problem started after I installed the updates for ubuntu... I have a hunch that its either the nvidia driver i installed or the latest kernel thats causing the problem. I'm using the proprietary driver for nvidia and my card is a GeForce6100 nForce 405... the kernel 2.6.35-22... help would be greatly appreciated, as you can imagine its quite annoying having the computer lock up..
P.S.- the freezes aren't exactly random, they happen generally when I'm using high CPU %'s (e.g. when i import all my music at once to rhythmbox and playing spring rts)

Sincere thanks in advance 
-Spencer

---

### Post by manters2000 on 2011-01-15
> **sdstolworthy said:**
> I've been using Ubuntu for a while now, and ever since I installed 10.10 (I did a clean install) I've been having problems with the computer completely locking up... nothing is responsive. I've not had this problem on any prior Ubuntu version. The problem started after I installed the updates for ubuntu... I have a hunch that its either the nvidia driver i installed or the latest kernel thats causing the problem. I'm using the proprietary driver for nvidia and my card is a GeForce6100 nForce 405... the kernel 2.6.35-22... help would be greatly appreciated, as you can imagine its quite annoying having the computer lock up..
P.S.- the freezes aren't exactly random, they happen generally when I'm using high CPU %'s (e.g. when i import all my music at once to rhythmbox and playing spring rts)

Sincere thanks in advance 
-Spencer

Got the same problem here...
Still got no solution.

---

### Post by sdstolworthy on 2011-01-20
Yep.. still nothing... i've scoured the internet... I can't even find a problem posted with similar descriptions.... it's a shame, really... this release is one of their best. alas, it's dampened by the fact that every time I actually want to do something somewhat important, the computer locks and I lose all of my work... It's very frustrating...

---

### Post by sdstolworthy on 2011-01-21
Okay I may have to eat my words, but I think I may have solved (if thats the word to use... kinda just stumbled on the fix) the problem. Anyhow, I completely removed the nouveau video driver, completely uninstalled my nvidia driver which I donwloaded from the website, and then installed the nvidia-current package. I also downgraded my kernel from 2.6.35-24 to 2.6.35-22. I haven't had a freeze in a couple of hours and was able to import my entire music library. Hope this works for you too.

---

### Post by MorrisseyJ on 2011-02-03
Spencer, i thought you were on 2.6.35-22 initially.

The reason i ask is because none of the kernels, other than 2.6.35-22 have worked for me. -23, -24 and now -25 have all given me the random freeze problem. -25 seems to be less of an issue than -23, in that i can work for longer before a freeze but none of them seem to work.

I am not sure if other people are having problems, there doesn't seem to be a whole lot out there on the forums.

I am also wondering if there is some bug i could report, possibly its the same piece of hardware which is causing problems on all the kernels. Does anyone know how i might identify this. 

If its a bug i'd like to get it reported so that it can go into Natty. In that regard i worry that i might install Natty in the future, have freeze problems, and then try and reinstall Maverick, and find only the latest kernel available.

---

### Post by beetlejuice321 on 2011-02-09
I to have had this problem as well. Its definitely related to the kernels. I have had lock up issues with several kernel versions now. searching the Ubuntu forums its looks like this is a common complaint. 

Its a pain because production users shouldn't have to mess with these bugs. New kernels are fine, but is it really warranted to update a new kernel every few weeks? Especially when the kernel fixes end up breaking other things.

---

### Post by garyjmellor on 2011-02-09
I have a Lenovo G550 2958 laptop with Nvidia GeForce G105M graphics. I have, in the past, installed the driver directly from Nvidia but this has caused me problems on occassion (never tracked it down). I recommend, if possible, to download the proprietary driver via Ubuntu itself if the system says one if available. I've found this to be the most reliable. Of course, my graphics are not the same as your so YMMV. Hope this helps.

---

### Post by kapetr on 2011-02-09
I have the same problem on one of my two PCs.
I is with VIA embed. graphic.

I will also test if just the X-server is death or whole PC.
I you can, try it too - by freezes try ping from another machine and let know.

BTW - my PC in +- 50% cases recover from itself after some minutes ...

--kapetr

---

### Post by beetlejuice321 on 2011-02-14
As I mentioned, I had this issue with Ubuntu and Nvidia's drivers. I believe is the Linux kernal. I just installed 64bit version of Fedora and without any proprietary Nvidia drivers and it had the same issue locking up!

I then just wiped the partitions again. This time I installed Ubuntu 32bit. System has been running on my laptop for hours, even went in to sleep mode, still no issues! 

I have been using 64bit Linux for years, yet still so many bugs...what gives? Actually there is probably very little benefit to using 64bit vs 32bit Ubuntu at this point anyways.

---

### Post by miroslav_karpis on 2011-04-04
Hi all, unfortunately having the same problem (10.10/64bit). Does anybody have some updates (very annoying)? Was it reported as bug?

---

### Post by Ghostlove on 2011-04-09
I, too, am having this problem.

I was running 10.10 64-bit before with no problems. I reinstalled it (from the same Live CD) a couple of days ago and since then have been plagued by freezing. It's happening loads, it's happened three times in the past hour. It's really frustrating because I can't do anything for very long as I keep having to reset my computer!

Has anyone got any ideas?

---

### Post by MorrisseyJ on 2011-04-09
Ghostlove:

What kernel were you running on? What kernel has installed with the fresh reinstall/first updates?

---

### Post by Ghostlove on 2011-04-09
I don't know what kernel I was running on. How do I find out which one I'm on now?

---

### Post by MorrisseyJ on 2011-04-10
Putting the following into the terminal:

> uname -a

Should give you some info looking something like:

> Linux (your computer name) 2.6.35-xx-generic-pae and some other stuff

That number is the kernel. I have had problems with every kernel since -22, so i have stayed using that one. 

With that in mind, if your system has been updating you have probably been using the most recent kernel. So i am not sure if this is your problem - maybe someone else has an idea.

You can still try installing an old kernel. I haven't actually had to do that (yet...), so don't have good instructions. That said, you'll probably find something on the web. If you can't find anything, posting that question as a new thread will likely get an answer.

If you try and install a new kernel, and it fixes your problem, do let me know how it goes. Good luck.

---

### Post by Ghostlove on 2011-04-10
Apparently I am using 2.6.35-28-generic. I will look up how to install a different one and come back to let you know how it went. :)

---

### Post by Pronker on 2011-05-10
I also have random system freezes. Full details here: [http://ubuntuforums.org/showthread.php?t=1703000&page=2](http://ubuntuforums.org/showthread.php?t=1703000&page=2)

I see more and more posts on this issue on ubuntuforums -- seems like this could be a problem at a very low level? I thought it was wifi-related at first but switching to a windoze driver @ ndiswrapper didn't help...

---

### Post by MorrisseyJ on 2011-05-10
You could try installing an older kernel - one that worked prior to one on which you are now having problems. 

I have yet to try this (i am waiting to submit a massive project, next week, before i install natty) so i don't know if it works. 

Instructions contained in this thread: [http://ubuntuforums.org/showthread.php?t=1739657](http://ubuntuforums.org/showthread.php?t=1739657)

---

### Post by frogo on 2011-05-29
> **sdstolworthy said:**
> I've been using Ubuntu for a while now, and ever since I installed 10.10 (I did a clean install) I've been having problems with the computer completely locking up... nothing is responsive. I've not had this problem on any prior Ubuntu version. The problem started after I installed the updates for ubuntu... I have a hunch that its either the nvidia driver i installed or the latest kernel thats causing the problem. I'm using the proprietary driver for nvidia and my card is a GeForce6100 nForce 405... the kernel 2.6.35-22... help would be greatly appreciated, as you can imagine its quite annoying having the computer lock up..
P.S.- the freezes aren't exactly random, they happen generally when I'm using high CPU %'s (e.g. when i import all my music at once to rhythmbox and playing spring rts)

Sincere thanks in advance 
-Spencer

Same problem (I think) on Dell Latitude e4310 with  2.6.34-020634-generic. 

Now and then the screen freezes. Rarely it requires hard reboot, usually it's a few seconds of unresponsiveness and then it comes back. It's often when using firefox, but I think not only. 

Sometimes, it's just firefox or a window (e.g nautilus) that'll become non responsive, being deemed or shaded. Then it comes back. But I don't know if it's the same thing that happens in those cases. 

In short, all things being equal, it's not unlike a typical Windows experience.  

I haven't seen any useful discussion of this, so fishing for pointers...

many thanks

---

