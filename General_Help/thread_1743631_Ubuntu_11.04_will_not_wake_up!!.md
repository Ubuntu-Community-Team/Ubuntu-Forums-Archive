---
title: "Ubuntu 11.04 will not wake up!!"
date: 2011-04-29
forum: General Help
---

### Post by JustMyAlias on 2011-04-29
again - new user - 2nd question today...
the first can go unanswered,
but this is a little more, uhh
critical??
I am copying all my files off my computer onto an external harddrive.
I know they are still copying due to the activity of the hard drive blinking light.
But my monitor/laptop has gone to sleep/ hiberbated/ whatever, and it will not wake up.  I don't want to power down and re-boot since I am in the middle of copying, and no idea where it will 'crash'.
Any thoughts??
TIA!
 
and I have done nothing with Ubuntu except install it - no code modifications...

---

### Post by aajv153 on 2011-05-02
same here: i even had to do a clean install to see if that would fix the problem - it did not. I changed the video card (both nvidia), and it even does it with the integrated mobo video. 
on ubuntu wake up, i get the background, but there are not icons, or bars, etc, just the background i had set before. if i double click i can access the usual short menu, i tried changign the background to see is that would bring the rest of the icons without success. 

i am using pentium d dual core, with 2g ram, 64 bit intall. 

justmyalias - what system do you have?

---

### Post by xoxbet on 2011-05-03
I have same problem on my Asus K52F laptop. I usually suspend it to ram (sleep) after working day, but I noticed, that after upgrade to 11.04 (kde) it does not wake up. One time waking it showed me background that was before sleeping (as mentioned above), but today it scared me with blinking colorful screen.

---

### Post by bwm5097 on 2011-05-03
I have a similar problem on an Acer Aspire One 522 Netbook.  After upgrading to 11.04, when I boot up I reach the grub menu.  But, when I try to boot in the new version it does not ever fully boot, the screen remains black and for a brief period a cursor is shown.  One time it showed my desktop background and nothing more, then start flashing different shades of a black screen as mentioned above.  When I boot into the most recent previous version it works (somewhat), but when I suspend it, it only wakes up to a blank screen.

---

### Post by aajv153 on 2011-05-03
On my work computer, (amd athlon dual core, 2 g ram), the update over the prior version gave the same problem, had to go to a clean install, it ended up working fine. 
The home computer, described above, I removed the video card and I am using the embedded video card, it boots to gnome, and works fine from there. 

any answers?

---

### Post by aajv153 on 2011-05-03
This is the erro i get when i try to install simple compiz manager:

simple-ccsm:
 Depends: python-compizconfig but it is not going to be installed
 Depends: compizconfig-settings-manager but it is not going to be installed

any suggestions?

---

### Post by calin_ionut on 2011-05-04
similar problem here. I have Ubuntu 11.04 with Gnome 3 (Gnome shell), i close the laptop lid (Suspend it to ram - sleep) and when open the lip the image is blur. I have to restart the laptop. 

Any idea how to this?

---

### Post by InHisName on 2011-05-04
I've just upgraded to 11.04 on my test box.  It is an older one, 2.0 ghz 2GB, single core.   Everything seemed fine. Ran a few apps and then had to do other things. Now its asleep and wont wake up.

Anybody found the proberbial virtual stick to poke at my alt-F7 gui to wake it up ?   I can get to alt-F2 in text mode but don't know how to wake it up yet.

---

### Post by calin_ionut on 2011-05-04
I installed [uswsusp]("http://suspend.sourceforge.net/") but the same thing. Even worst...the system became unstable....gnome-shell use 100% of CPU if it`s not gnome-shell it`s gnome-settings-daemon. I don`t understand why. Remove the uswsusp application and everything came to normal. 

Suspend is not working for me!:(

---

### Post by InHisName on 2011-05-04
Gave up and held in button and ended.
Hung again,  rebooted.   dirty disks, long time, errors, more time.
Rebooted and shutdown 3x.  All appears to work ok now.
Tried Pidgin, ok its running and I can get back from screen saver mode.

Seems ok so far. . . .

---

### Post by InHisName on 2011-05-05
Seems that getting a login prompt from screen saver works.

BUT after a LONG while, it seems to go into a deeper sleeping status. Probably not hibernate as power still running, fans turning, motherboard power led lit.  No monitor sync active.  Mouse has power when moved, the led get brighter.

Possibly suspend, but I apparently do not know the key combo to wake it up. I have tried many, ctrl-alt-F1 to F12, ctrl-alt-del, ctrl-alt-backspace, many others.   Also tried power button for less than 2 seconds. Still nothing.

---

### Post by rtmie on 2011-05-13
I am seeing a similar problem after upgrade. (Desktop based on ASUS motherboard with  AMD Phenom(tm) II X4 965 Processor

Will not resume from suspend in response to mouse or keyboard entry, but will with short press to power key IFF done immediately after suspend.

However if in suspend for a while goes completely dead, fan still running and main power light on but no response to short press on power button, ctrl-altF1 or no ping response over network.

Only solution is to reboot.:confused:

Am a long term linux user at work and home with various distros and a few years on Ubuntu, but cannot find anywhere to start chasing this down.

Also before seeing this thread had seen many on suspend/resume problems but none like mine til now.

Getting very fed-up.

Rob

---

### Post by rtmie on 2011-05-14
I have followed the steps in [[COLOR="Green"]this post[/COLOR]]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")  relating to 10.10 and so far so good, no problems on suspend resume since last evening.

Rob

---

### Post by rtmie on 2011-05-14
Spoke too soon, Another lockup, got 24 hours this time, but problem still there.

R

---

### Post by artoonie on 2011-05-27
Any updates on this?


> My KDE log file has this at the top:
CMM_COMMAND_UNLOCK_SURFACE failed: [67]!
Could not release surface
CMM_COMMAND_UNLOCK_SURFACE failed: [67]!
Could not release surface
 ddxSigGiveUp: Closing log

Can't guarantee that this is related but it seems to be?

---

### Post by Rebelli0us on 2011-05-27
All my new machines would NOT suspend/resume properly until I disabled USB3 in BIOS.

---

### Post by nozema on 2011-06-01
Same problem here, no problem when screensaver is active only a couple of minutes, when longer, no activity and I have to turn of PC...

---

### Post by vuetrip on 2011-06-08
Did anyone fix this as have had this quite a lot in the past few days.

It's as if the computer is still awake but not waking the monitor - maybe problems with driver.

If I go System => Administration => Additional Drivers 
 it says: NVIDIA accelerated graphics driver(version 173) [Recommended] which is installed but at the bottom to the left of the remove button it says "This driver is activated but not currently in use"

how do I make it "currently in use" so I can try sort this out as like others posting above I have to hold the power button in and restart the computer as it never recovers from going into the screensaver.

Thanks

---

