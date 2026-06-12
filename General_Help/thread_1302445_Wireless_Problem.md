---
title: "Wireless Problem"
date: 2009-10-27
forum: General Help
---

### Post by gco211 on 2009-10-27
Hey all, I just switched to Linux and installed Ubuntu jaunty.  Windows screwed with me one too many times, and I'm generally really liking the customization and simplicity of the OS.  I know simplicity might not always spring to mind, but frankly, for anyone with google and a basic knowledge of reading and computers, the terminal is amazing.  

Anyway, I've been having a problem in KDE as far as wireless goes. I know this has been a known problem, and I tried searching this forum and a general google for this, but all their solutions, while alluding to my problem, aren't working for me.  Basically, wireless works great in Gnome but not at all in KDE. I installed Kubunti by installing kubuntu-desktop and those associated files.  I've also installed knetworkmanager, and the globe appears in the bottom right toolbar (sorry, I'm not good on the terminology yet), but it just continuously tries to connect to the wireless signal (it does detect it.  I also, tried using Gnome's Network Manager, but that also was unsuccessful.  

Has anyone had this problem and had a successful solution?  

My other question, and maybe this is just a difference between Windows and Ubuntu, has to do with fonts.  I installed that Microsoft basic fonts package, but the fonts still look odd in FireFox.  It's not a huge problem, but it is a bit off putting and if anyone could point me in the direction of a good guide on the matter I'd be very appreciative.  

Thanks a lot!

---

### Post by gareththegeek on 2009-10-27
Have you tried using wicd, which is a replacement network manager. It should be listed in the package manager.

I was having trouble with network manager connecting and reconnecting constantly and solved it by using wicd.

---

### Post by gco211 on 2009-10-27
> **gareththegeek said:**
> Have you tried using wicd, which is a replacement network manager. It should be listed in the package manager.

I was having trouble with network manager connecting and reconnecting constantly and solved it by using wicd.

BINGO!   You are the man.  I feel so dumb for asking that question.  I honestly spent two hours trying to figure that out (half of it switching between Gnome and KDE since I could only use the internet with Gnome).  Thank you so much.

---

### Post by fraserstaple on 2009-10-27
Hey Gco.
  	 	 	 	 	 	  I am Fraserstaple and I read your entire pasting. According to your problem I am suggesting that download [FONT=Helvetica]SuSE’s new release version        8.0 which is Linux Standard Base (LSB) compliant, built on Linux kernel 2.4.19, glibc 2.2.5, and        gcc 3.2. In the 8.0 release, gcc 3.0 was still dubbed “experimental” and        gcc 2.9 was the default compiler.After doing this, I think You got the solution of your problem. Anyways Thanks.
[/FONT]

---

