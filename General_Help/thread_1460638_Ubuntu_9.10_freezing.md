---
title: "Ubuntu 9.10 freezing"
date: 2010-04-23
forum: General Help
---

### Post by SmokeyMcpuff on 2010-04-23
I installed Ubuntu 9.10 on my new desktop pc (i-3 @2.93, 1TB HDD, Raedon HD 4300, 4 gb ddr2).. the problem is it randomly freezes at different points of time randomly.

Mostly, it freezes while using firefox and opening too many tabs. Or it might freeze as soon as I log-in. The other time it has frozen is while i had firefox and the media player open.

I'm new to Linux, however, the auto updater has updated the kernel, and the graphics card. I read somewhere else in the forums it might be because I have desktop effects on, could that be a reason?

Also, during the freeze I cannot do anything - except move the mouse. The mouse will not click. Keyboard doesnt respond, and Cntrl+alt+del doesn't work either.. I have to do a hard reset (sometimes more than 2 because it will freeze after log-in).

Please help!

---

### Post by P4man on 2010-04-23
If your mouse still works, its not really a freeze (kernel panic). If it happens, do not do a hard reset, instead use REISUB:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

(dont think your keyboard does nothing just because X windows isnt responding to keyboard input, REISUB will probably still work).

Anyway, thats not a real solution of course. Best thing to do is narrow the problem down, and indeed disabling desktop effects would be one of the first things to try. Go to system > preferences > appearances > Visual effects and set it to none. See if it still happens.

Other things to do, go to system > adminstration > log file viewer and look up the events right before the freeze. Particularly check "messages" in there and xorg.0.log (perhaps attach or copy paste that one here).

---

### Post by SmokeyMcpuff on 2010-04-25
Well, I turned graphics to medium and things seem to be going well.

The system is stable most of the time and I use REIUSB to re-boot each time the kernel panics. However, still have a problem during boot sometimes where the screen just goes blank (this is pre-login screen, but post-splash screen), REIUSB works here as well, but I was hoping for something to stabilize it permanently, i.e. no crashes whatsoever. How/why is the system crashing at boot?

I've attached the xorg.0.log as requested. Thanks!

---

### Post by P4man on 2010-04-25
its not stable "most of the time" if this happens more than once every year! Turn desktop effects completely OFF. Extra or normal are pretty much the same thing, as afaik, they both use compositing features of your 3D card. IF you set it to none, see if the problem persists (quite possible, but lets rule out one thing at the time and 3d drivers are a common cause).

Ill check the logs later.

---

### Post by SmokeyMcpuff on 2010-05-06
So I moved the desktop visual effects back to none, but of no avail, the system still stalls randomly.

Now, its become worse, where the system stalls on boot itself for up to 3-5 boots (I reboot using REISUB). 

I ran memtest too, and came up with no errors.

How do I get this to work? 

I'm thinking I might just give 10.04 a shot.

---

### Post by zdave on 2010-05-07
After trying the 9.10 remix, on my laptop running directly from a cd and finding out it ran well, I decided to load it on my laptop, create a dual boot, and my Ubuntu system now runs "only" in Failsafe... if at all. Sometimes I have to totally resort to the keyboard to get anything to work.  I'm sure it must be a driver, or drivers, particularly video.  Once I find out what the hardware problems are can I configure and fix things from xterm or better yet boot into the command line interface and fix them there??  I've gotten lazy with Ubuntu 8.04 LTS working so well....on my desktop.  Oh, and Smokey....., Knoppix runs well on the laptop-- without the 3d stuff even off a USB flash drive so I know with persistence I should be able to eventually be running smoothly again.  I post back when I get it running smoothly.  

Any other ideas?

---

### Post by zdave on 2010-05-14
O.K. perhaps there is no one seeing this thread anymore...  However I did say I'd post back when I had a solution, so  ....
While trying to upgrade the 9.10 remix with synaptic it froze solid while installing the upgrades. (Still think it was a driver; probably video) Long story, short, lost everything including my ability to boot the laptop normally.  So I got out my super grub disk cleared out grub to just have windows boot, then got my linux partition clean with gparted which is on Knoppix.  Went back to a U 8.04LTS, Hardy Heron CD and installed it via the expert or non-guided way.... creating a dual boot between Windows XP (yes, I still need XP sometimes for work):( and Ubuntu 8.04.  Thus far it has been working well.  Probably did not have to use gparted but I learned some things along the way.  And I've got 6 months before I need to start thinking about upgrading again.  Hardy has been true to its namesake.

---

### Post by SmokeyMcpuff on 2010-06-08
Well After upgrading to 10.04, the system is alot more stable. I had my first crash since my upgrade a month ago today. Again, while running firefox, this time without any 3D, or composting enabled.

---

