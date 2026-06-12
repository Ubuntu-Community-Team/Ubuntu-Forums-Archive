---
title: "Computer won't boot post-Ubuntu installation, MBR problems?"
date: 2010-06-23
forum: General Help
---

### Post by DGarret on 2010-06-23
Hey guys, badly in need of some help here. I've sort of worked out what the problem is after a late night of screwing around (kind of a Linux noob here) is but lacking the knowledge on how to fix it. So, the short of it:

I tried to install Ubuntu as a dual-boot on my Windows XP machine, using the USB stick trial OS and automatic installation. My screw-up came when I left my external USB hard drive plugged in during the install, and as far as I can tell, Ubuntu was installed on that as opposed to my internal HD. Now when I try to boot, I get knocked straight to the grub rescue prompt with an error message that basically shows my "no such device (my external's ID)" -- assuming that the MBR (which I know nothing about editing) is trying to boot off the external that isn't actually enabled until an OS starts it up, and dumping me at the rescue prompt when it can't find it.

I can still load up the trial Ubuntu off the original USB stick (though can't get online with it without wireless drivers), but that's as functional as the computer gets right now. And I don't have a Windows Setup CD anywhere (using a rooommate's Mac at the moment with a terrible European keyboard on it). So is there any way to edit the MBR or something to tell it to boot my regular XP off my internal HD, at which point I can re-partrition and try this whole thing again, or otherwise remove the failed install of Ubuntu through the trial-stick or... well, I'll leave the suggestions up to you all. I've been working on this since about 4am last night and my brain is kind of fried. ;)

Thanks so much in advance for any help, stuck in a real bind here, hoping to get it fixed before my roommate gets back from work and needs her laptop back! Much obliged, guys.

---

### Post by C.S.Cameron on 2010-06-23
Can you boot with the external plugged in?
There should be a grub option to boot Windows.

What you would like to do is get a copy of the XP install disk, start Emergency Repair Console and then type "fixmbr".

Any XP install disk should work.

Otherwise I have used an application named "ms-sys", (Google it, it may be hard to find). 
It will restore the XP MBR if you are booting from the Ubuntu Live CD.

The Emergency Repair Console is simplest and safest.

---

### Post by DGarret on 2010-06-23
Thanks for the reply, been googling my *** off to try to figure the problem out (and solutions).

Booting with the external drive plugged in isn't working -- the computer/grub isn't "recognizing" the drive and reports it as "not found", at least not until a full boot using the Live Cd/stick "enables" it.

Seems like the Windows CD is the best option to fix the MBR, problem is I don't have one (damn OEMs) and am having trouble finding anything online. To add insult to injury, my CDR drive is old and kind of wonky, making burning much of anything a problem.

I've mostly been trying to find a way to boot the Windows HD through Grub (I can always make a recovery CD once I get into Windows), but the rescue mode it's kicking me out to isn't the most useful, none of the commands I'm finding are work in it -- got a million instructions on how to do it through a full working copy of Grub, but having trouble booting into that.

I'll check out the ms-sys thing you mentioned now, my other tentative idea was trying to put just grub on another USB stick and booting the internal hard drive off of that. Guess I'll just keep hammering away at random ideas until one works (or a friend finds a damned XP CD)!

Thanks again, any more ideas are always appreciated. Least I'm learning a lot through the process -- always said best way to figure out a computer is to break it and have to fix it again yourself! :)

---

### Post by DGarret on 2010-06-23
For the record, got it solved (mostly)! Just downloaded Super Grub Disk to boot off of, loaded Windows off of that. Now I just need to fix the MBR so I don't need the boot disc every time I restart, but that's no biggie. Gotta say, now that I'm back in slowed-down-Windows-hell I'm kind of missing Ubuntu already. I'll retry the dual-boot install later and hopefully do it right this time. Thanks for the help!

---

