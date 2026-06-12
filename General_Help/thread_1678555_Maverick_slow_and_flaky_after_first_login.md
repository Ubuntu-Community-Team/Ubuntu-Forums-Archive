---
title: "Maverick slow and flaky after first login"
date: 2011-01-30
forum: General Help
---

### Post by Eksilius on 2011-01-30
Shortly before Christmas, I bought a brand new gaming computer for dual-booting Win7 and Ubuntu. After testing the 64-bit Maverick live CD and finding it flaky, mildly put, I still opted to install it on a desdicated hard drive as planned. After enabling the proprietary Nvidia drivers installing the regular updates, adding the Ubuntu X-swat PPA and generally stretching both my patience and my imagination as far as I can, I'm left with one very annoying problem:

To start with, the first login after boot is notably slower than subsequent ones. I mention this because it might be related to the real problem, which is that the first time I've logged in after each boot, my desktop's multitasking capability seems to be gone. If I open a link from Gwibber or an email, my browser opening will steal the focus entirely and I'm not able to switch windows or even move any window (including the browser window) until the browser has been closed (sometimes requiring Ctrl-Q as I can't use the menus). Going on for a while, the whole desktop will eventually freeze. If left alone for sufficiently long, It might recognize my next command but at that point, I've usually lost my patience and restarted the machine (Ctr-Alt-Del strangely always works).

The only workaroyund I've found is to log in the first time after boot, then log out immediately, then log in again. The second login is blistering fast and the desktop is super-responsive with no further problems. Very odd in my opinion.

I've tried to reinstall Ubuntu without any improvement. I've tried to run the 32-bit Live CD but it's just as flaky as the 64-bit. Linux Mint Live is just as flaky as Ubuntu, and Fedora 14 live doesn't even boot although it runs super-fast under Virtual Box (as does Ubuntu 10.10...) An old Xubuntu 9.04 Live CD is the first thing in my collection that boots without problems.

Is this all about having too shiny new harcdware? I've got an Asus P7P55D-E LX motherboard, A Core i5 processor, and an Nvidia GTX460 graphics card. Anybody with similar experiences and perhaps a tip, please let me hear from you.

---

### Post by xdevnull on 2011-01-30
I have a similar setup p7p55d-e pro and 2 gtx 460's in SLI and an i5.  I had problems with the network card and some quirks with the video that I'm running to an older hdtv via dvi.  I installed the binary driver for the network card to get the networking going and turned on vsync to blank.  I can't get it to suspend properly - but so far I haven't had the performance issues your experiencing.  Have you tried install the previous version of ubuntu - Lucid (10.04), it is an long term support version and is supposed to be less flaky.

Right now I'm having some issues with video going blank when I first turn the system on and then login (everything up to that is fine).  It seems that after it "warms up" it works fine.  Interestingly the monitor still seems to detect a signal - it's just blank.  It's odd.  Maybe a cable/connection issue.

---

### Post by Eksilius on 2011-01-31
I've tried the live CD for Lucid but it was just as flaky as Maverick. I don't think it would be the solution although I haven't tried to install it on the hard drive. I have a feeling it's related to Xorg or gdm somehow but I cannot say for sure. Any further tips are much appreciated.

---

### Post by konaya on 2011-03-04
I have this exact same problem on my system. But it hasn't always been like this; this started happening only a few days ago. The only link I seem to have to you guys is the processor family (i have an i3).

Pretty much everything else is different, I think. It's a Sony VAIO (geek politics aside, this was the only laptop that met my hardware tests when I snuck around in computer stores booting floor models off live USB sticks). Intel graphics, 4GB RAM, nothing unusual.

Worth adding is that I use the 2.6.36 from the kernel ppa (so that I can use my internal microphone).

---

### Post by Eksilius on 2011-03-06
Aside from the desktop PC that has the problem, I have a Vaio too. It has an AMD Athlon II P340 and ATI graphics, however, not Intel hardware. And it runs Maverick without any problems whatsoever (I thought Intel/Nvidia was to be a safer bet but no). It also smoothly runs Unity directly from a live CD of Natty Alpha 3 whereas the desktop PC falls back to standard Gnome and is just as Flaky as Maverick. Truly frustrating. I've opened bug #720863 over this issue but nothing seems to happen. If you've got the same problem, please go to Launchpad and notify the developers that this bug concerns you. That should help add a little urgency to solving the problem.

---

### Post by Eksilius on 2012-01-01
Just as I was going to, finally, post a new bug for Oneiric, I realised that the computer was actually behaving as it should. Failing to identify any recent updates as something that should have magically fixed it, the only recent change to be thought about was that we'd given it a new mouse for Christmas.

Consequently, I plugged in the old mouse, which had been used since the computer was bought, and rebooted just to find that the old problems had returned. I then connected a third mouse that we have in the household, rebooted again, and voila: no stability problems at all.

So the original bug has now been closed. Next time I run into mysterious problems of any kind, I'll make sure to try another mouse before I go posting in any forum or in Launchpad...

Happy New Year to all Linuxers alike!

---

