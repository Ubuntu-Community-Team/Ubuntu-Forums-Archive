---
title: "Freezing at desktop picture (please help me!!)"
date: 2009-07-31
forum: General Help
---

### Post by jeb800e on 2009-07-31
:confused::confused::confused:

I have downloaded Ubuntu 9.04 via Install inside Windows. Each time I go to run Ubuntu, everything seems to work until the desktop image is shown. That is when it freezes up and won't do anything. The first time the mouse was shown. I unplugged and plugged in the mouse again to see if that would help, which it did not. I then restarted my PC to try *again*. Once again, it froze at the desktop picture, but this time with no mouse shown. Can anyone PLEASE help me out here?!

(edit)
Also, each time I have ever tried the LiveCD, the loading screen would come up, then, once it was all loaded, it would seem to glitch up or something, as the top (I would say) 25-30%portion of the screen would be black, and the rest would be similar to what you see as static on the TV, but it isn't moving. Inside the "static", I can see the Windows logo up, yet it is all screwed up and clustered around in a certain area, like it needs to be re-aligned to fit, almost like a puzzle.

Maybe Windows has been trying to "take over" while using the LiveCD?

---

### Post by Kai Summers on 2009-07-31
This could be a problem with your install, try reinstalling.
Otherwise create a livecd. Just download the iso and use something like MagicISO to burn it to disk. This will create a CD that you can use to boot into a working version of ubuntu. Just insert the CD and restart the computer. Ubuntu should then load from the CD if you have got your BOOT order setup corrently.

---

### Post by jeb800e on 2009-07-31
I installed from a requested CD from Ubuntu.

Each time I have ever tried the LiveCD, the loading screen would come up, then, once it was all loaded, it would seem to glitch up or something, as the top (I would say) 25-30%portion of the screen would be black, and the rest would be similar to what you see as static on the TV, but it isn't moving. Inside the "static", I can see the Windows logo up, yet it is all screwed up and clustered around in a certain area, like it needs to be re-aligned to fit, almost like a puzzle.

Maybe Windows has been trying to "take over" while using the LiveCD?

---

### Post by jeb800e on 2009-08-01
Can someone please help me! I may be planning on ditching my Windows for Ubuntu, but I want to make sure this will work properly until then!
I will try re-installing Ubuntu right now.

Please help me! Thanks!

---

### Post by jeb800e on 2009-08-01
bump...

---

### Post by jeb800e on 2009-08-01
I reinstalled it, and several times. None of them worked correctly, acting the same as the times before. I was able to easily boot up my Ubuntu *7.10* LiveCD, though. I wonder what the problem could be?

Ubuntu 7.10 was did not recognize my wireless card.

Please help me out here! Thanks.

I am using an ATI Radeon 9600 graphics card, 1 GB RAM, about a 70 GB HDD, and a Belking Wireless-G Desktop Card. Also, a Turtle Beach Riviera Sound Card.

---

### Post by jeb800e on 2009-08-03
Can anyone please help me?

---

### Post by GnuSense on 2009-08-05
I think I am having a similar issue.   I upgraded from Intrepid to Jaunty, upon rebooting I got as far as the graphical KDM login manager, then I noticed that my keyboard wasn't working.  Neither was the mouse.  I figured it was an Nvidia issue, I have an rather old Nvidia video card: 

NV11 [GeForce2 MX/MX 400] (rev b2)

So I booted to rescue mode and did a "apt-get remove nvidia*" and rebooted but same stuff.  I booted to the command line, logged in as root, tried fooling around with different versions of xorg.conf or none at all, same keyboard and mouse freeze, even after disabling DontZap in the xorg.conf.  Trying to start GDM or simple start the GUI with startx led to the same problem.  The mouse would be responsive at first, then all I would get is a white dot where the mouse had been.  Using the Magic SysRq sequence I could reboot, but couldn't get in to the GUI. 

 So I noticed that there were other kernels listed in grub so I tried  2.6.27-14-generic and the GUI booted just fine, even at 1680x1050, using the nv driver.  I haven't tried reinstalling the proprietary driver (I'd have to use the older 96.43 version of the nvidia driver).  I'm not sure what the proprietary driver would get me, compiz didn't work on Intrepid and I'm not a gamer.

So jeb800e, what I'd suggest is when the computer first boots up to the GRUB screen, use the down arrow key to select an older kernel. The default that did not work for me was:
  vmlinuz-2.6.28-14-generic

FWIW, I have an Athlon XP 2500+ with an ECS Nvidia nForce2 chipset.

---

### Post by jeb800e on 2009-08-06
Okay! Thank you so much! I will try this as soon as I can and I will post an update, if possible.

---

### Post by GnuSense on 2009-08-06
If you don't have a handy dandy alternate kernel listed in your grub menu.lst it should be possible to boot to the shell (rescue mode, I guess it is called) and install a new kernel that you can try.  It seems that there are several in the repositories.  I'm on a Hardy box right now and seem to have the choice between about six versions of 2.6.24, 2.6.24-18 through 2.6.24-24.  If you need more specific instructions post back here & I can walk you through it.

---

### Post by jeb800e on 2009-08-06
Yeah, I just got around to trying to start the Ubuntu 9.04 LiveCD. I can't find anything about using alternate kernels within the CD itself, and I am new to Linux, so if you can help me, that would be great! Thanks!

I was maybe thinking Windows was trying to take over somehow, as (like I said before), I can see the Windows logo all scrambled up behind all the frozen static on the bottom 70-75% (I would guess) portion on the screen. The top portion is blank without static.

If I mess around with the settings and options before I boot up the LiveCD, I can clearly see the distinct Windows Xp colors and the scrambled up logo and some text underneath it. It looks like it may say "Windows is slowin..." and I can't read the rest, much.

---

### Post by jeb800e on 2009-08-07
bump...

---

