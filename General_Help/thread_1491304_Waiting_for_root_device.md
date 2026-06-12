---
title: "Waiting for root device"
date: 2010-05-23
forum: General Help
---

### Post by DragoneyeIIVX on 2010-05-23
On booting, I'm getting this error: 
Gave up waiting for root device. Common problems: 
(( A list of possible checks, none of which help me))
ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxx2e6aa does not exist. Dropping to a shell! 

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
(initramfs) _
--- 
I just installed Lucid from Karmic, overwriting everything, and this is the first time I've experienced this. Looking around on Google didn't yield much, and my normal 'go-to' Linux buddy wasn't able to figure out what was wrong. 

Any ideas? Thanks in advance, and for the record I'm not terribly Linux-able, so please humor me with specifics on how to do things :) 

Edit: Adding in what I've seen from the rest of these forums - 
- I've reinstalled twice now. 
- I don't see the Grub Loader, it just blinks the underscore for about 2 minutes before coming up with the error message. *(No longer true, I was able to get it functioning)*
- Typing exit doesn't do much - brings up a white screen (even waiting on that screen for 3-5 minutes doesn't help). 
- Booting from a live disk just brings me to the same screen.  *(Unless I chose nomodeset in the menu - then it just keeps bringing up the error)*
- This is the only thing on the HDD, so couldn't conflict with other OS's.

- Going into recovery mode I get SRST failed (errno=-16)

Moar editing: 
Now attempting this suggestion. 
[http://ubuntuforums.org/showthread.php?t=1399810&highlight=Gave+waiting+root+device](http://ubuntuforums.org/showthread.php?t=1399810&highlight=Gave+waiting+root+device).
Failed. I can change it to root=/dev/sda1 ro (etc etc) then ctrl-x then input exit, to try and bypass the problem, but I get a white screen after it loads. Note however, that this white screen also comes up when I try to boot a live CD without enabling nomodeset, so this might be a graphics issue as well. 
Graphics card is a nVidia GeForce 9500 or thereabouts. 

When I do this, the "ALERT!" changes to: "ALERT! /dev/sda1 does not exist. Dropping to a shell!" 

Readout of boot info - 
[http://pastebin.com/6HK7Yynj](http://pastebin.com/6HK7Yynj)

New attempt - 
I pulled out an old HDD and put Lynx on it. I don't get the error message on bootup, but even with nomodeset I still get the white screen, though half the time it fails to boot (I'm going to call this an issue with the HDD most likely, though).

---

### Post by DragoneyeIIVX on 2010-05-23
Shameless bump, with updated information.

---

