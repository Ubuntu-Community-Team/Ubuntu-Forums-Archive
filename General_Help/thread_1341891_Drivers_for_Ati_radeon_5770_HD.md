---
title: "Drivers for Ati radeon 5770 HD"
date: 2009-11-30
forum: General Help
---

### Post by Hugolin on 2009-11-30
Hi thats my video card Ati radeon 5770 HD, anyone else have one and knows how i install the drivers for it? >_<
i did the lspci | grep VGA thing and it says:
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68b8

dunno maybe that helps!
well ty for any help you can give me!
(oh i forgot, i have ubuntu 9.04, and i dont use 9.10 because video dont work there, and when i fixed it , mouse and keyboard didnt work, so ill stay with 9.04 for now)

---

### Post by mikewhatever on 2009-11-30
ATI has a driver for you with installation instructions link.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English)

---

### Post by detlev24 on 2010-01-01
hello,

i installed the ati driver (9.12) on ubuntu 9.10 x64 and encounter the following problem:
as soon as i restart the system, the video display is about twice the size of my monitor (dell u2410) which means the resolution (1920x1200) is kept but the image does not fit on the panel. i always need to change to a lower resolution and afterwards switch back to 1920x1200 to get the image fit the monitor size (until next reboot...).

what can i do? thx and a happy new year. :)

---

### Post by skytja on 2010-01-03
Hi,

The problem is in the AMD Catalyst driver; it does not currently support x-server 1.7 // xorg 7.5.

I have the same issue with regards to the screen resolution.  I also get these raster lines where it is like the screen is 'folded' and the information is duplicated.  Hard to describe.  I have been trying to get my 5770 card to work since October, but no joy.

I am trying to experiment with the 9.11 drivers /w patches.  no luck yet, but I have heard of other people who have had success.  The forums over at phoronix are friendly.  [http://www.phoronix.com/forums/showthread.php?t=21029](http://www.phoronix.com/forums/showthread.php?t=21029)  A number of AMD developers frequent the radeon forums there.  From what most of them are saying, this probably won't work until Ubuntu 10.4 is released.

---

### Post by dbaran on 2010-01-05
Hi,

With my HD5770 I have been using the ATI 9.11 drivers ( downloaded and installed from their web page) it worked flawlessly in my x64 Ubuntu 9.10 so far.

However, I tried installing ATI 9.12 last week and it didn't work so I had to switch back to ATI 9.11. I hope they will address the problems with 9.12 in the next release/patch.

---

### Post by dbaran on 2010-01-07
... by the way hot-fix for 9.12 did not work either.

---

### Post by MikeyOT on 2010-02-12
Hi fellow sufferers!

I'm currently running 64-bit Kubuntu 9.10 having just switched from Suse 11.2 to try out Grub 2 and because I thought that 11.2 was a bit of a let down after quite a good run of releases.  I'd been using linux since Linus released the first version (xenix, unix and minix before that), nothing but Suse since 7.0.  With these I used nVidia cards practically since my Tseng Labs ET4000 (is that right - I'm getting old and the memory is fading lol) went south.

I'd seen that ATi linux drivers now existed and the 5770 came at a really great price.   I also had a friend who always swore ATi were better than nVidia but then he only used Windows so I shouldn't have listened to him!  I thought there wouldn't be a problem since my nVidia cards had always worked in the past.  My main problem is that with my former nVidia card I ran two monitors side by side - a 1680 x 1050 and the second a 1280 x 1024.  No problems at all.  Now with the 5770 in, the signals from the two digital outputs go to both monitors at the same time and the cursor jumps from one monitor to the other at random intervals.  I have to manually disable the second monitor.  The main monitor then works fine, but, obviously I am not happy.  I got used to all that real estate.

Last ATi card I shall buy, that's for sure, but I'll keep it for a while and see if they release a fixed version of the Cat drivers.  If that's not soon then I can see me breaking my other long-standing loyalty - to AMD.

Mikey

ps Nothing wrong with the latest 64-bit Windows 7 Cat drivers <spit>

---

### Post by Mark Phelps on 2010-02-12
Apparenly, the new 10.1 Catalyst drivers are out.  You folks should all go to the AMD/ATI site, download those, and try those out.  These are supposed to have corrected the X-server problem that plagued the earlier versions.

---

### Post by neoanderthal on 2010-02-19
I just picked up and installed a pair of HD 5770 cards to use in Crossfire for my Windows gaming partition. I downloaded the 10.2 Catalyst update for Linux, and the 5770s work fine (even allowed me to enable Crossfire under Linux).

If you're running one of the newer ATI cards, I would definitely recommend Catalyst 10.2

---

### Post by dert on 2010-03-26
> **neoanderthal said:**
> I just picked up and installed a pair of HD 5770 cards to use in Crossfire for my Windows gaming partition. I downloaded the 10.2 Catalyst update for Linux, and the 5770s work fine (even allowed me to enable Crossfire under Linux).

If you're running one of the newer ATI cards, I would definitely recommend Catalyst 10.2

Can you or another reader please provide the link to download the x64 10.2 Linux Catalyst update?  That would be awesome.  Is it available from the Synaptic Package Manager?

---

### Post by qblake on 2010-04-21
I get the Unsupported hardware watermark, ant if i try to run aticonfig, i get no supported adapters found.  Plz help.  If this doesn't work, I just wasted $160 for nothing!!

---

### Post by clhsharky on 2010-04-21
HI qblake

What cat driver and what card?

Sharky

---

### Post by canac on 2010-06-20
I'm fairly new to Ubuntu/Linux, and installing drivers for this card has been giving me headaches for days. I had absolutely no luck installing or running Ubuntu 10.04, so I switched to 9.10, with the intent of *maybe* upgrading to 10.04 after I get everything working on 9.10, but I can't even get things working on 9.10. I downloaded Catalyst 10.6 and followed the given instructions, but when I get to the final step, running "/usr/bin/aticonfig --initial," I get the following message: "/usr/bin/aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor."

Any suggestions? Thanks very much.

---

