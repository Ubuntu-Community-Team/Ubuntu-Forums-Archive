---
title: "Monitor goes to sleep right after boot"
date: 2009-07-30
forum: General Help
---

### Post by miguel64086 on 2009-07-30
This is a very weird one.
I have Ubuntu 9.04 and this started happening right after a mandatory reboot after some package updates.

The PC goes to GRUB and after I select Ubuntu, it start to load and right before the desktop is suppose to appear, it the monitor shuts down, as if the video card stops sending a signal. The monitor then goes into power saving mode and shuts down.
After a few secs, I can hear the ubuntu music that indicates it finished loading.
At that point I can SSH and I can use VNCViewer to remote to the desktop... but I can't use the actual monitor attached to the PC.
it's driving me nuts!
I can even access my files on my Samba share!

Any help would be appreciated.


DATA

Current Version:
Linux <host> 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

attached are the specs of my hardware

---

### Post by t4thfavor on 2009-07-30
Try going to a tty, by pressing ctrl+alt+F1 and then logging in.
 
You can then check the dmesg output, and do a bunch of other stuff to figure out whats causing the video to go haywire. 

If you get brave you can reconfigure the xserver-xorg package, and you may get your video back.

---

### Post by miguel64086 on 2009-07-31
OK... every time I post something, I realized that I forgot to say something...
1- I  did try ctrl+alt+F1 with no luck.
2- I can dual boot into Windows XP with no problems... but who would want to do that!  ;)
3- I recently upgraded the RAM from 1 GB to 4 GB... it worked for a while... but once in a while I get a message at the BIOS saying "overclocking failed".  I bought this PC at this local store and I'm afraid they overclock it to make it faster than it is and didn't tell me.  But why would they don't tell? I mean... they didn't charge me for it...  I don't know how to overclock it, even of course I don't know how to revert it either.  I guess that would be my last option.

I'll check hte dmesg tonight. thank you

---

### Post by miguel64086 on 2009-08-02
Ok...
I got the DMEG output, but either I don't know what I'm looking for (quite possible), or it doesn't show a bit.


The only two things that I notice are:
1- [   25.960858] [drm:i915_setparam] *ERROR* unknown parameter 4
[   25.960890] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   26.911438] [drm:i915_getparam] *ERROR* Unknown parameter 6

which according to [this link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341363") is a known bug.

2- AMI BIOS detected: BIOS may corrupt low RAM, working it around.
which I have no clue what it means


I can access TTY after all... but I cannot go back to the gnome desktop.

Additionally, I tried uninstalling the gnome-desktop and reinstall it... no dice.

Please help, I don't want to go back to windowz cause once I saw the light... I can't go back...  thank you

---

