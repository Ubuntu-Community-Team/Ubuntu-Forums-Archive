---
title: "Some thoughts about 64bit vs 32bit and available RAM"
date: 2011-12-03
forum: General Help
---

### Post by kansasnoob on 2011-12-03
I've googled quite a bit about this and I honestly think this is the most reliable source:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

I recently acquired my first 64bit hardware:

[http://ubuntuforums.org/showthread.php?t=1864833](http://ubuntuforums.org/showthread.php?t=1864833)

(Yes I'm poor) :)

But this low-end 64bit hardware has only 2GB of RAM and I find that using the i386 version of Ubuntu still delivers better performance overall than the 64bit version, particularly regarding RAM usage.

When I run the 64bit version RAM usage quickly climbs to 50% or 60% while performing the same tasks using the i386 version generally results in RAM usage of less than 30%.

Is this normal?

I'd really appreciate some feedback so I can gain some understanding about this. Naturally the simple answer is to use whatever works best for you :D

---

### Post by oldtimer7777 on 2011-12-03
I have always used 64-bit whenever possible. Even on low end systems with tight specs like your hardware.  No issues. No problems.  It is always related to installation issues with 64-bit Ubuntu deb packages like Google Earth and Citrix ICA deb and 32-bit deb packages that won't install in 64-bit, and forcing installations with 32-bit libraries on 64-bit installed Ubuntu OS, and never about performance issues. Also, having to use ndiswrapper to install Win drivers that are only 32-bit and not 64-bit sometimes can be a pain. But the latest kernel seems to have more of the older drivers than it did a couple of years ago, so perhaps that issue has been resolved. Having a freshly installed HDD always has made the biggest difference on older systems because that is one of the last things users will upgrade until absolutely necessary, and if it is a laptop then it is almost required to swap out the used hard drive for a new one, to save a headache later on. If a laptop is older than 2-3 years, it is time to upgrade the HDD to a new drive, if there is any doubt about the potential for constant usage. 

> **kansasnoob said:**
> I've googled quite a bit about this and I honestly think this is the most reliable source:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

I recently acquired my first 64bit hardware:

[http://ubuntuforums.org/showthread.php?t=1864833](http://ubuntuforums.org/showthread.php?t=1864833)

(Yes I'm poor) :)

But this low-end 64bit hardware has only 2GB of RAM and I find that using the i386 version of Ubuntu still delivers better performance overall than the 64bit version, particularly regarding RAM usage.

When I run the 64bit version RAM usage quickly climbs to 50% or 60% while performing the same tasks using the i386 version generally results in RAM usage of less than 30%.

Is this normal?

I'd really appreciate some feedback so I can gain some understanding about this. Naturally the simple answer is to use whatever works best for you :D

---

### Post by kansasnoob on 2011-12-03
> **oldtimer7777 said:**
> I have always used 64-bit whenever possible. Even on low end systems with tight specs like your hardware.  No issues. No problems.  It is always related to installation issues with 64-bit Ubuntu deb packages like Google Earth and Citrix ICA deb and 32-bit deb packages that won't install in 64-bit, and forcing installations with 32-bit libraries on 64-bit installed Ubuntu OS, and never about performance issues. Also, having to use ndiswrapper to install Win drivers that are only 32-bit and not 64-bit sometimes can be a pain. But the latest kernel seems to have more of the older drivers than it did a couple of years ago, so perhaps that issue has been resolved. Having a freshly installed HDD always has made the biggest difference on older systems because that is one of the last things users will upgrade until absolutely necessary, and if it is a laptop then it is almost required to swap out the used hard drive for a new one, to save a headache later on. If a laptop is older than 2-3 years, it is time to upgrade the HDD to a new drive, if there is any doubt about the potential for constant usage.

Do you think increased RAM usage is actually a good thing then?

I mean, if you have 2GB of RAM but almost never use it why have that much RAM :confused:

This is just new to me :)

I must say that I love my first nVidia graphics chip. It takes a bit longer to set things up but afterwards it's worth the trouble :)

---

### Post by oldfred on 2011-12-03
Linux uses RAM as cache, so I so not think RAM usage is a good indicator. It assumes whatever you were doing you may do again, so it leaves it in memory until that memory is needed for something else. And only if all RAM is used by currently active applications does swap then get used. So many times RAM use may be high but not because you are currently actively using it. Not sure if there is a difference between 32 & 64 bit on how it manages RAM or not.

---

### Post by kansasnoob on 2011-12-03
> **oldfred said:**
> Linux uses RAM as cache, so I so not think RAM usage is a good indicator. It assumes whatever you were doing you may do again, so it leaves it in memory until that memory is needed for something else. And only if all RAM is used by currently active applications does swap then get used. So many times RAM use may be high but not because you are currently actively using it. Not sure if there is a difference between 32 & 64 bit on how it manages RAM or not.

Hey there old friend, long time since we last met :D

This is just one of those things where I'm personally going into "uncharted territory". Eerrm, probably a bad way to say that :(

Uncharted for me ............ I'm clueless. The only thing I know is that running the 32bit version of Ubuntu seems to be flawless, whereas the 64bit version seems "flaky", particularly with flash video.

You know I'm no true noob to Ubuntu but I just wondered what I should be expecting. As I said before, I'll use whatever works best for me ............ no problem there, and you know I love the testing :D

---

### Post by oldos2er on 2011-12-03
> **kansasnoob said:**
> ncharted for me ............ I'm clueless. The only thing I know is that running the 32bit version of Ubuntu seems to be flawless, whereas the 64bit version seems "flaky", particularly with flash video.


Are you using 64-bit flash, or 32-bit with ndiswrapper? I've had no flash problems for a long time using 64-bit.

---

### Post by oldfred on 2011-12-04
I know a lot of people have reported issues with flash, but I have not had any that I know of. 

I run the 64 bit version on my laptop with only 1.5GB RAM just so I have the same version as my 4GB Desktop. Both have not given any issues that I can say are due to flash or the difference. I still have every version from 9.10 in some 20GB partition, but currently use Maverick as my main install. My wife was complaining about too many changes, so I stopped, but plan on a converting to 12.04. So far 12.04 seems ok, but I assume much of the breakage is yet to come.:)

My last 32 bit install was 9.04 and that was upgraded from 6.06 every 6 months and all the cruft was more of an issue. It really needed major housecleaning or it made the change to a clean 64bit look even better.

---

### Post by cap10Ibraim on 2011-12-04
I used to have 32 bit scientific linux that can see more than 4 gb ram and still use 5% 
while 64bit use 11 % 
I guess you already read [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
also windows 7 64 bit require min 2gb ram , while window7 32 bit require min 1gb of ram 
, so I think out of the box 64 system will use more RAM , if you have less than 4gb 
better to stick with 32 bit system

---

### Post by kansasnoob on 2011-12-04
Today I seem to have two separate issues going on. The first is flash related, both on 32bit and 64bit installs, and on two totally different sets of hardware. Basically Oneiric flash just keeps crashing, but my Natty installs are fine playing the same flash videos.

The second is related to memory usage in the 64bit Oneiric install, but I need a few days to do some repeat testing. It certainly seems almost like the 64bit Oneiric kernel may have a memory leak because if I leave the computer running overnight with no processes running the memory usage creeps up from about 20% to 60 or 70%.

But I'm going to be busy for a few days so I'll have to get back to this later. Until then I'm glad I multi-boot, that way I can always boot something that just works :)

---

### Post by oldtimer7777 on 2011-12-04
> **kansasnoob said:**
> Today I seem to have two separate issues going on. The first is flash related, both on 32bit and 64bit installs, and on two totally different sets of hardware. Basically Oneiric flash just keeps crashing, but my Natty installs are fine playing the same flash videos.

The second is related to memory usage in the 64bit Oneiric install, but I need a few days to do some repeat testing. It certainly seems almost like the 64bit Oneiric kernel may have a memory leak because if I leave the computer running overnight with no processes running the memory usage creeps up from about 20% to 60 or 70%.

But I'm going to be busy for a few days so I'll have to get back to this later. Until then I'm glad I multi-boot, that way I can always boot something that just works :)

Did you try installing and running the flash aid plugin script for Firefox yet on 11.10?  Do a google search for Firefox Flash Aid Plugin. Sometimes it helps fix these kinds of flash issues.

---

### Post by Rsjc741 on 2011-12-04
Back to OP:

My thoughts have always been that 64-bit services take more memory to run. Same for x64 programs.

I'm not sure why though... possibly the more threads an individual program uses, the more memory needs to be allocated towards that computation.

Just my guess

---

### Post by oldtimer7777 on 2011-12-04
> **Rsjc741 said:**
> Back to OP:

My thoughts have always been that 64-bit services take more memory to run. Same for x64 programs.

I'm not sure why though... possibly the more threads an individual program uses, the more memory needs to be allocated towards that computation.

Just my guess

It is double, but I hardly every run anything that requires more than 4Gb just surfing the net and maybe fooling around with Gimp..   It sure is faster.

---

### Post by kansasnoob on 2011-12-05
I tend to think from all I've read, my own experiences, and the fact that I have only 2GB of RAM on that 64bit hardware that I'm likely better off sticking with i386 ......... but:

I'd mentioned needing a few days to deal with other issues. The first two of those are performing a hardware clean-up, you know - cleaning the dust bunnies out of my computer cases (particularly the fans and cooling fins), and I need to fix a friends computer that's been sitting here for a couple of months (he's using my "loaner" and I need it back).

So, given RAM compatibility, while cleaning my boxes (one of which was filthy) I needed to swap some RAM around to come up with a stick to test in this friends box.

WOW, after cleaning my boxes, swapping some RAM around, etc, my performance on both machines is much improved :)

Oddly on my somewhat older Intel 32bit box I reduced the RAM to 1GB from 2GB and it can now do the same flash video at less than 50% of RAM, but most surprisingly the CPU runs at about 85% instead of 100%.

That puzzled me enough that I put in the other 1GB stick (the one I need to use for testing the friends box) and after doing so running the same exact flash videos results in about the same RAM usage but increased CPU usage :confused:

Just to be sure I didn't have a failing stick of RAM I swapped the two and get the same result. Totally odd I guess, I'd always thought more RAM was always better, but I'm just a do-it-yourselfer when it comes to computers ;)

On the 64bit machine, which was obviously still fairly clean, it's much more responsive with the RAM I just swapped in. Now, I always check compatibility when either purchasing or reusing RAM, but most of us know that manufacturers are not always correct.

So I still need to do more testing, but I think it's fair to say RAM compatibility and cleanliness can and will have a great impact on performance. It may also be worse for me because the humidity is incredibly high in my current environment, so connections can get "tarnished" quickly.

I do find it incredibly odd that on this Intel Atom box I actually seem to get better performance with 1GB of RAM than 2GB of RAM. Any hardware engineers out there?

I wish I could go back to school and learn more about just how this all works :lolflag:

---

### Post by oldos2er on 2011-12-05
> **kansasnoob said:**
> I tend to think from all I've read, my own experiences, and the fact that I have only 2GB of RAM on that 64bit hardware that I'm likely better off sticking with i386 

I ran 64-bit Ubuntu on 2GB RAM for almost a year, and it ran great. CPU-intensive tasks like video encoding were measurably faster than they were on 32-bit. For day-to-day tasks like web browsing, email, etc., you probably won't notice much difference. 

I'm not sure how the myth that 64-bit requires 4GB or more RAM got started, but it's a shame it got started at all. In the mid-nineties if you had a machine with a 64-bit PowerPC CPU, I guarantee you had far less than 4GB RAM. :)

Edit: Have you run memtest on your RAM, just to rule out any problems?

---

### Post by cap10Ibraim on 2011-12-05
> **oldos2er said:**
> I ran 64-bit Ubuntu on 2GB RAM for almost a year, and it ran great. CPU-intensive tasks like video encoding were measurably faster than they were on 32-bit. For day-to-day tasks like web browsing, email, etc., you probably won't notice much difference. 

I'm not sure how the myth that 64-bit requires 4GB or more RAM got started, but it's a shame it got started at all. In the mid-nineties if you had a machine with a 64-bit PowerPC CPU, I guarantee you had far less than 4GB RAM. :)

Edit: Have you run memtest on your RAM, just to rule out any problems?
It's not a myth , the thing is that those who write the kernel such as Windows kernel will assume that if you have 64 bit system , then you have more ram , so upon startup they'll load more things into ram to make your experience more responsive and faster

---

### Post by kansasnoob on 2011-12-06
@ oldos2er,

I hadn't thought to run a memtest because I seemed to have a problem only in Oneiric 64bit, but since swapping these sticks of RAM around (for a totally unrelated reason) things seem to be working great. In hindsight I wish I had run a memtest :)

I'm marking this solved now, but will change that later if the problem resurfaces.

---

### Post by dcstar on 2011-12-06
64-bit hardware can utilise RAM very efficiently **if** it is installed and configured correctly.

You will see multiple notes in motherboard documentation telling you to use matched sets of RAM modules and then to specifically put them in particular RAM slots. There are usually also BIOS settings to change the way the RAM is presented to 64-bit systems.

Before anyone makes judgements on performance of 64-bit systems they better make sure that they actually have their systems configured correctly.

---

### Post by ofnuts on 2011-12-06
> **cap10Ibraim said:**
> It's not a myth , the thing is that those who write the kernel such as Windows kernel will assume that if you have 64 bit system , then you have more ram , so upon startup they'll load more things into ram to make your experience more responsive and fasterNot really... what happens is that a lot of the data the CPU handles and keeps in memory are addresses (what programmers call "pointers"). In a 64-bit system these are stored in 8 bytes instead of 4, so apps and the system will always use more memory for the same functionality.

---

### Post by oldos2er on 2011-12-06
> **cap10Ibraim said:**
> It's not a myth , the thing is that those who write the kernel such as Windows kernel 

Windows? This is an Ubuntu forum, we're talking about Ubuntu.

---

