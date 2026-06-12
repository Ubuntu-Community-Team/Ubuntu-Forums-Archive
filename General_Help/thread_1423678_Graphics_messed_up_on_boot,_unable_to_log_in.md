---
title: "Graphics messed up on boot, unable to log in"
date: 2010-03-06
forum: General Help
---

### Post by levells on 2010-03-06
I just bought a Radeon HD 3650 graphics card to replace my old Nvidia one (and to run two monitors).  The first time I booted it up after switching, it was fine.
I installed the flrgx (I think that was the name of it but I might have swapped a letter or two) that someone said to and the linux edition of the command center (amdcccle or so).
It said it needed a reboot.  I turned my computer off and then back on.  It let me go to the grub menu like always and it starts booting Ubuntu 9.04 like normal.
It gets to the logo and the orange progress bar. Once the progress bar fills up, the graphics start messing up.  Little images of the graphics bar tile the top half of the screen and the color is all messed up (mostly green).
I tried typing like I was logging in but nothing happened.  I tried to go to the terminal with ctrl+alt+f1, but nothing happened then either. I tried recovery mode, attempting to update/upgrade things, ran fsck, tried repairing graphics problems, and almost any other option that I thought might help.
Unfortunately, nothing worked.  Is there anyway I can fix this so I can at least log on? At this point I just need to log on so I can write a paper. I can handle sucky graphics until I have time to fix things.

---

### Post by flippo on 2010-03-06
Ohh those last minute papers on a broken PC, I've had a few...

If you HAVE to work NOW, try running an old kernel, I suspect it will work slightly better.

To try and fix your problem, after a buggy boot please post the output of /var/log/Xorg.0.log

That may give us some clues as to what is going horribly wrong.

---

### Post by levells on 2010-03-07
How would I be able to get the output of that file?  Right now, the only way I can do anything is to use recovery mode and drop to a root terminal.
Cat works but I can only see a limited amount of the file (lines 739 to the end at line 761)

---

### Post by patchwork on 2010-03-07
You can use nano, or boot from a live cd, mount the / partition, and view the log there

---

### Post by levells on 2010-03-07
Okay, the liveCD didn't work.  I end up with the same results-- the messed up colors and frozen screen.
And the older kernel didn't work either.  Both 2.6.28-18 and -11 give the same result.

Nano seems like it works but would I have to type all those lines?  Or is there a way I can copy the log file to my external hardrive? I tried cp /var/log/Xorg.0.log /media/Simpledrive

Edit: I just managed to copy it to my windows partition. I'll post as soon as it restarts.

---

### Post by patchwork on 2010-03-07
Try ```
cp /var/log/Xorg.0.log /media/Simpledrive/Xorg.0.log
```


PS.   make sure you mount the Simpledrive first

---

### Post by bikodog on 2010-03-07
I had this very same problem recently installing a Radeon 4300 video card.

The ubuntu help page below was my general resource for getting it up and running:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

When I had the locked-up screen problem, I booted into recovery mode and ran the following from the terminal:

```
$ sudo apt-get remove --purge xorg-driver-fglrx
```

After rebooting, I could at least get back to normal graphics until I could repair the issue

---

### Post by levells on 2010-03-07
Okay, here's the log file.

---

### Post by patchwork on 2010-03-07
I didn't see anything indicating a problem in your log.   Is this happening on one screen or both?  Have you tried temporarily trying a lower resolution (I know it's not 3d, but may be causing problems similar to this, from your log:>    	 	 	 	 	 	  (II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf 

---

### Post by levells on 2010-03-07
It does it to both screens. I can't remember what the resolution for the first monitor is but the second one is the one I've always had and I'm pretty sure that one is at 1280x1024.
Would attempting to use xrandr possibly help? Or would that not work from the console?

---

### Post by patchwork on 2010-03-07
xrandr won't do any good without the x server running.

I'm going to paw through your log again, but right now I'm stumped.   You could try what bikodog suggested, but removing the proprietary drivers seems drastic (although the general feeling is that the fglrx driver causes problems)

---

### Post by levells on 2010-03-07
I did what bikodog suggested but that didn't do anything either.
Correction: something changed slightly.  When I try and boot it like normal, I at least have a mouse now.  But I still can't try and log in.

---

### Post by patchwork on 2010-03-07
The only thing I see in the log is that the Radeon dri module failed to load, but a substitute framebuffer loaded in its place....

EDIT:  >    	 	 	 	 	 	  (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): using shadow framebuffer 

I'm not sure this loaded in its place, might just be another related module...trying to find information right now

---

### Post by patchwork on 2010-03-07
Maybe something here will lead you in the right direction....

[http://dri.freedesktop.org/wiki/DriTroubleshooting#head-6b3fa13adc97ea201a9129246e6ea7739848ec73](http://dri.freedesktop.org/wiki/DriTroubleshooting#head-6b3fa13adc97ea201a9129246e6ea7739848ec73)

I'm not sure where else to go with this, and am not even certain that the DRI/ DRM error is the cause of all of this.

---

### Post by levells on 2010-03-13
I was just looking over the system requirements for Ubuntu and it keeps saying a VGA graphics card. That was what my previous card was but the new one is DVI-D. Does that mean I can't use Ubuntu with this card at all?

---

