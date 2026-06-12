---
title: "Doom 3 will not run."
date: 2009-11-04
forum: General Help
---

### Post by darkshadow on 2009-11-04
I just bought a new laptop and I am trying to run Doom 3 on it, but it will not start due to a segmentation fault will initializing opengl.

I have a GeForce GTS 250M video card and running Karmic 64bit with Nvidia 190.42 drivers which are the newest and only ones to support this card. Compiz runs fine and I did try disabling it before running doom

Here is the console output when running doom3


----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
idRenderSystem::Shutdown()
double fault Segmentation fault, bailing out

---

### Post by khelben1979 on 2009-11-04
Which version of Doom 3? 

And I hope that you're trying out the Linux version and not trying to run it through Wine for example (might get problematic).

---

### Post by Giblet5 on 2009-11-04
Are you running x64 Ubuntu?

The doom3-linux bits are about half that.

---

### Post by darkshadow on 2009-11-04
I am running the newest Linux binaries and yes I am 64 bit, but I checked and I have the 32bit libraries installed for libGL under /usr/lib32. According to the official info the doom3 binaries will work on a 64 bit environment.

---

### Post by Giblet5 on 2009-11-04
Well, once you get past that libGL.so.1 error, you're likely to hit the libstdc++.so.5 brick wall that stopped me. I tried cheating on that. I linked the one from an old vmware installer. gamex86.so still doesn't like the version...

Once they release the full source code, I'll just build it again. Until then, there's that noisome "Windows XP" grub menu item I can fall back on.

---

### Post by darkshadow on 2009-11-04
I got it to work. I had installed the drivers from Nvidia's website since I require the newest to support my card, but it seems there was some problem with the install (even though Compiz and Tuxracer worked) so I added a PPA that had packaged the newest 190.42 drivers for Karmic then I got farther into the boot but gave different problems. Which was fixed by adding myself to the "video" group. After that it works perfect and I can play.

Now to get used to FPS's again since I have not played them since Doom 3 first came out and believe me I just played for a few minutes and could not hit the broad side of a barn.

---

### Post by khelben1979 on 2009-11-05
I assume you get pretty good performance with that card?

---

### Post by darkshadow on 2009-11-05
For performance I have only tested a couple resolutions for about 5 minutes each.

1280x720 gets roughly 60fps
1920x1080 is roughly 40fps

both set to ultra quality on a native 1080p 18.4" laptop screen
a couple other system specs that have a little effect core i7 720qm 1.6ghz processor and 4GB of ram vid card had 1GB dedicated

---

