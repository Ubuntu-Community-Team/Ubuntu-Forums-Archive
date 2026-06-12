---
title: "System Dies - Monitor emits flashing line pattern"
date: 2010-07-07
forum: General Help
---

### Post by siabost on 2010-07-07
Hiya,

I have installed Ubuntu 10.04 on a Dell Dimension 2350/ 2Ghz P4/ 1.5GB memory.

After running for up to 10mins the system dies and the monitor alternates between black & a half-screen display of vertical black & white bars every second or so (first the top half then the bottom half of the screen). The unit has the standard Intel onboard graphics chip.
The same happens with Ubuntu Studio & Xubuntu yet Mepis 8.5 & Fedora 13 run without problem.

It's a standard installation of Ubuntu & all updates have been applied.

Anyone have any ideas or experienced something similar?

Thanks.

---

### Post by dnguyen1963 on 2010-07-07
> **siabost said:**
> Hiya,

I have installed Ubuntu 10.04 on a Dell Dimension 2350/ 2Ghz P4/ 1.5GB memory.

After running for up to 10mins the system dies and the monitor alternates between black & a half-screen display of vertical black & white bars every second or so (first the top half then the bottom half of the screen). The unit has the standard Intel onboard graphics chip.
The same happens with Ubuntu Studio & Xubuntu yet Mepis 8.5 & Fedora 13 run without problem.

It's a standard installation of Ubuntu & all updates have been applied.

Anyone have any ideas or experienced something similar?

Thanks.

Search this forum for random freezes.  There are over 600 posts regarding this problem.  There might be a solution for your system in all those posts.  In the mean time, try the following...set the screen saver to none...set the power management to never...do not use compiz.

Good luck.

---

### Post by siabost on 2010-07-07
Thanks dnguyen1963

The onboard graphics has no 3D driver loaded so Compiz isn't active.

I will try the search you suggest.

Ta

---

### Post by satish_j on 2010-08-26
> **siabost said:**
> Hiya,

I have installed Ubuntu 10.04 on a Dell Dimension 2350/ 2Ghz P4/ 1.5GB memory.

After running for up to 10mins the system dies and the monitor alternates between black & a half-screen display of vertical black & white bars every second or so (first the top half then the bottom half of the screen). The unit has the standard Intel onboard graphics chip.
The same happens with Ubuntu Studio & Xubuntu yet Mepis 8.5 & Fedora 13 run without problem.

It's a standard installation of Ubuntu & all updates have been applied.

Anyone have any ideas or experienced something similar?

Thanks.

This is exactly the problem iam also facing after installing 10.04.Earlier,with 8.04,I never faced any such prob.
Did you find the solution to it?
I have searched a lot w/o any success

---

### Post by watcheroftheskies on 2010-09-07
Hi,

I&#7743; a Mint user myself, but i saw yor post on Ubuntuforums so here is my reply to a similar post on Linux Mint forum:

"I had the same problem with my old Dell Dimension 2400 (2003, I  think...). I first had Mint 7 on it (Perfect) and after some messing  around with other distros I decided to put Mint 9 on it. Ok, while  working on it. But after leaving it alone for a while I came back and  saw these flashing white bars at the top halfof an otherwise black  screen. After some searching I finally found: 

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Because  of the workaround changing the kernel I decided to give the latest  Ubuntu Maverick Beta1 a go > solved the whole problem! So it the  kernel all right.
But Ubuntu doesn't match the streaming video  capacity of Mint (even with restricted extra&#347; installed) so I  re-installed Mint 9 and got the latest maverick kernel 2.6.35... This  made my system crash when changing the screensaver... So, downgrade to  9.6.31 then (onother workaround in the wiki ubuntu )? This gave an error  at boot (couldn find /home...) Now finally I installed Mint 8 (kernel  2.6.31) and my problems are gone... I&#7743; still convinced the problem lies  with the 2.632 kenel in Mint9/Ubuntu10.04

So my advise would be:

-  Install Mint 8 for now and wait for Mint 10 based on Ubuntu Maverick.
or
-  Give Ubuntu maverick beta1 a go.

PS. Hope you weren't tempted to go back to 'the Dark side'";)

regards,

watcheroftheskies

---

