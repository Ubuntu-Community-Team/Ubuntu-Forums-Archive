---
title: "Hope this is an easy fglrx question"
date: 2006-01-28
forum: General Help
---

### Post by newclique on 2006-01-28
Since I am running Breezy right out of the 'box', I notice when in Synaptic that I am not running the fglrx driver but rather the Radeon and ATI components (and I do not get DRI although all logs say the ATI and Radeon components loaded successfully). 

So, if I want DRI then I need to upgrade the driver. However, if I select the newer fglrx package (xorg-driver-fglrx) and mark the original driver for removal then it says it will remove Ubuntu desktop, and x-window-system-core. I'm not sure I want to do this. Should I? Any 'gotchas' I need to know about.

---

### Post by jasay on 2006-01-28
[QUOTE=newclique]Since I am running Breezy right out of the 'box', I notice when in Synaptic that I am not running the fglrx driver but rather the Radeon and ATI components (and I do not get DRI although all logs say the ATI and Radeon components loaded successfully). 

So, if I want DRI then I need to upgrade the driver. However, if I select the newer fglrx package (xorg-driver-fglrx) and mark the original driver for removal then it says it will remove Ubuntu desktop, and x-window-system-core. I'm not sure I want to do this. Should I? Any 'gotchas' I need to know about.[/QUOTE]
Don't worry about Ubuntu-Desktop as it's a metapackage.  It has no actual code, just depends on everything that's in a normal install (makes it easy to install the x/k/ed/ubuntu desktops and their respective apps.)  The x-window-core I believe is rather important though (assuming you like to have more than a command line).  Just install the fglrx driver and the kernal restricted modules for your particular kernal ("uname -r" in a terminal to find out which kernal you're using.)  Unless you're really pinched for space, you might as well leave the radeon/ati driver there as I think it would be a major pain to remove without borking x.  [Here's]("http://www.ubuntuforums.org/showthread.php?t=75378") a good howto if that doesn't make sense.

---

### Post by newclique on 2006-01-28
Well, I did it. Now what happens is that I get a black screen. I can tell X is doing something because my monitor displays the frequency change to 60 (for 1280) or 75 (for 1024 or 800). In the Xorg.0.log, DDC returns all pertinent information about my monitor so I'm not sure why it isn't syncing up. If I drop the resolution all the way down to 640, I get a screen....but it does not finish rendering all of the Gnome desktop before the mouse and keyboard locks. I can toggle the CAPS lock key off and on but outside of that, I cannot escape X. 

If anyone knows of a definitive list of softlinks and libraries that must be in place for the DRI not to hang (and use ATI's rendering library versus Mesa), I would be very grateful. This may be a software issue.

Two other things: When I boot into recovery mode and run "cat /proc/mtrr" I get just one line that would seem to correspond to just my system memory:

reg00: base=0x00000000 (0 MB), size= 512: write-back, count=1

Nothing about the video ram.

Also, when I "lspci | grep ATI" I get a line that says:

PCI bridge : ATI Technologies Inc.: Unknown device 4243

This is the line that is the most suspicious to me.

Thank you guys very much.

---

### Post by newclique on 2006-01-29
Well, I tried the suggested /proc/mtrr fix from here:
[http://ubuntuforums.org/showthread.php?t=115104](http://ubuntuforums.org/showthread.php?t=115104)

but no luck. I get a 'file system is read only' when the /proc/mtrr fix takes place. 

I really think that the mtrr issue is the likely culprit if indeed I should be seeing 3 entries for cat /proc/mtrr and not just one.

---

### Post by newclique on 2006-01-29
With Ubuntu, that is. I have a live eval of Suse 9 and it boots immediately into 1280x1024 and it recognizes my 8500 and the mtrr records are correct (there are 3 of them at least). I don't have DRI but after sinking probably 50 hours into trying to solve the 3D issue with Ubuntu, it is obvious that the problems are with the OS in some capacity, possibly the setup procedures, not the card. 

There are so many distros of Linux that it makes no sense to keep at this. I would urge anyone else having trouble with their video or other hardware to keep trying distros until they find one that works with everything. This is far simpler and smarter than trying to debug this stuff endlessly even if it is possible to eventually get it to work. With a family and kids, this is ridiculous. And I really want to become a Linux user if not an exclusive Linux user.

Honestly, I think the problem lies with the extra requirements and modularity of kernel 2.6. If was trying to get a dual core or 64 bit proc running then I would probably have no choice but to go with 2.6 but I suspect that is not the case for the majority of users.

See you on the dark side, Luke!

---

