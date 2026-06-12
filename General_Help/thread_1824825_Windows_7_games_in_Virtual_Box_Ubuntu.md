---
title: "Windows 7 games in Virtual Box Ubuntu"
date: 2011-08-14
forum: General Help
---

### Post by SkidMarkHavoc on 2011-08-14
Hi, I am thinking of getting a dist of linux, and have chrosen Ubuntu, because it looks awesome, but need some assistarnce. I am an extreme gamer, and am wondering if I can run my current windows 7 pre 64-bit in a program like virtualbox or VMWare on Ubuntu 10.04 64-bit, and still run games, LAN to windows machines, play online, and run programs like Steam from it. Also, would I have to install drivers in a virual machine running Windows, or just Ubuntu? And how well will games run compared to windows? Also, I run my internet connection through a PPPoE connection on my desktop on windows, will Ubuntu also support this feature?
 
 
My specs:
MSI AMD/ATI Radeon HD 5970 2GB
AMD Phenom II X4 970 @ 4.2
8GB DDR3 1333
1TB 7200RPM HDD 64mB cache
CD/DVD ROM
720w Gigabyte PSU
 
Everything works fine in windows, and I never lag in any games, except Crysis and Crysis 2, but only minimal lag (40FPS)
 
Many thanks,
SkidMarkHavoc

---

### Post by mendhak on 2011-08-14
Hi Skid, short answer is that you should dual boot.  Because the graphics drivers are being emulated through software, you won't get very good performance at all.  In most cases, you won't be able to go full screen and there will usually be mouse pointer or rendering issues.  In some cases, old games are known to work fine, but none of your newer titles will work.  

Assigning plenty of hardware to the VM won't help if the VM itself wasn't designed for this purpose.  I've got an i7 2600K with a GTX 580 myself and had spent a few days trying to do everything within Ubuntu itself before deciding to boot into Win7 when I wanted to play something.

You will have the option of running some games in Ubuntu itself.  For example, WoW runs alright, and if you bought the Humble Indie Bundle, those games run quite well.  If you look at the [appdb on winehq]("http://appdb.winehq.org/"), you'll see that they've gotten some games to work in Wine.  HL1, HL2 and Portal1 worked fine for me, your mileage may vary. For everything else, dual boot.  It's not worth the hassle and the quality just won't be as good.

---

### Post by woodyg on 2011-08-14
>   In most cases, you won't be able to go full screen and there will usually be mouse pointer or rendering issues.I haven't had any such problems. Otherwise I agree though. But for everyday Windows tasks, e.g. Office, Photoshop etc VirtualBox works like a dream. No issues.

---

