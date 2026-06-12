---
title: "proprietary driver makes desktop spill offscreen"
date: 2010-08-05
forum: General Help
---

### Post by drammock on 2010-08-05
SYSTEM DETAILS
I'm running Ubuntu 10.04 64-bit, with an Nvidia Quadro FX 580 graphics card, and a fairly big screen (1920x1200).  Fresh out of the box (using the built-in Nouveau driver) everything looked fine, by which I mean the top and bottom panels were where they are supposed to be, at the top and bottom of the screen.  But to enable desktop effects I was asked to install one of the Nvidia proprietary drivers (my choices were "version 173" or "version current").  I have tried both (both installed through the Admin > Hardware Drivers GUI), with the following results:

PROBLEM DESCRIPTION
When using the proprietary drivers, the fancy desktop effects look great, but the edges of my desktop are offscreen (including the top/bottom panels).  By adjusting the height property of the top and bottom panels I have deduced that the desktop extends about 42 pixels above and 42 pixels below the limits of my display, and likewise to the left and right (though I haven't measured the sides precisely).  I can move my mouse offscreen and still click on things, knowing roughly where the various menus are supposed to be even though I can't see them.

WHAT I'VE ALREADY TRIED
The first thing I checked was the Nvidia X-server settings, which were set to "Auto"; no change if I manually set it to 1920x1200 to match my monitor's native resolution.  I tried various other resolutions with mixed results (in some lower resolutions the panels at the top and bottom of the screen were visible, others not).  I looked around the [Nvidia Linux forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"), but couldn't find anyone with this problem.  Then, based on [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") I tried actually purging the Nouveau driver from the system, even though that is supposed to be unnecessary under 10.04, but there was no change.  I also tried downloading a driver from the Nvidia website (NVIDIA-Linux-x86_64-256.44.run) and installing it via terminal as described [here]("http://us.download.nvidia.com/XFree86/Linux-x86_64/256.44/README/index.html").  That also did not work (though I forget the details of what went wrong; as I recall I never got it properly installed).  EDIT: see next post for details of what happens with the downloaded driver.

After discovering this problem I have since wiped/reinstalled 10.04 due to a mistake in setting up a Win7 dualboot, and the display problem persists.  But I now have Nouveau back, and when disable the proprietary drivers I can once again see the edges of my desktop when using Nouveau.  But I want to get the desktop effects working under the proprietary driver (mostly for Docky, but also for some of the desktop switching effects).  Any advice?

---

### Post by drammock on 2010-08-07
UPDATE
Yesterday I tried installing the driver from the Nvidia website again.  Details of what happened:

(1) during install, I got an error "the distribution-provided pre-install script failed.  Continue anyway?"  (I said yes)

(2) "Install Nvidia 32-bit OpenGL compatability libraries?"  (I said yes, though since I'm running a 64-bit system this gave me pause)

(3) "run X-config and write new values (backing up old ones)?"  (don't remember the exact wording of this question but that was the gist of it...  I said "yes")

After all that and a reboot, I got this error:
"(EE) NVIDIA(0) failed to initialize the NVIDIA kernel module.  Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.  ***Aborting***  Screens found, but none have a useable configuration."

Then I got the "Ubuntu is running in low-graphics mode" dialog.  I looked through the kernel log, but couldn't decipher anything that looked like it was giving me any more information than the original error message already had (though perhaps I just don't know what to look for).

Any help is greatly appreciated.

---

