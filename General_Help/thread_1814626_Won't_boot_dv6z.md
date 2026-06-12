---
title: "Won't boot dv6z"
date: 2011-07-29
forum: General Help
---

### Post by dougrose on 2011-07-29
I have a new HP dv6z, A8 processors.

I am trying to boot Ubuntu 11.04, using flash drives from osdisc.com.

I get the language selection screen followed by the Ubuntu menu screen.  I select "Try Ubuntu without installing", and the screen goes blank, followed by the Ubuntu logo over one red dot and three white ones.  That is as far as I get.  No more red dots.

Results are the same if I select "Install Ubuntu".

I have tried a 64-bit usb drive, and also a 32-bit version, with the same results.

Am I doing something terribly wrong here?  Is there an option or something that I am missing?

         *      *      *

I tried downloading the 64-bit .iso file from canonical, using another ubuntu machine, and making a boot dvd.  I get the same results as above:  the ubuntu boots as far as the ubuntu logo, then freezes and goes no farther.  Is there an option or something that will make it work?  If not, is there (should there be) a list of hardware that ubuntu will not work on?

---

### Post by relay_man on 2011-07-30
Hi dougrose

I did a little searching and looking around, and I'm not completely sure but it seems your hardware may be a little too new.

Look here:    [http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=2](http://www.phoronix.com/scan.php?page=article&item=amd_a83850_graphics&num=2)

Like I said, I'm not completely sure.

I would advise you to do a little more research and verify my theory.

Sorry I couldn't offer something a little more encouraging.

---

### Post by dougrose on 2011-07-31
I have been able to boot and install Ubuntu 10.4.3 AMD64 and it works fairly well.

I needed to scare up a driver for the wireless from Broadcom, and I have no control over the parameters for the video, but it is working.  The display flickers occasionally, and I have no idea if that is a driver problem, or something in the hardware.  I have not noticed the flicker when playing movies.

I cannot use 2-finger scrolling, it does not seem to be part of this release.

I do not know if I will be able to move up to 11.04.  I will report my progress in this thread.

---

### Post by dougrose on 2011-08-01
The dv6z saga continues:

I have been able to update my ubuntu 10.04 install to 10.10 and then to 11.04.

However, 11.04 tells me that I do not have the hardware to run the new interface, so I am still using the pull-down menus.  Apparently, quad processors and dual video cards are not enough for Unity.  Wireless works, but some video functions do not.  The screen still flickers periodically.

At this point, I would not recommend that anyone buy this hardware to run ubuntu.  More later.

Late flash:  I have now installed the ATI/AMD video driver and the system comes up in Unity.  There is still an odd flicker in the screen: every ten seconds or so it dims for just a moment.  I really don't think that this is hardware, it's not regular enough.  I still need to finish loading out and testing my apps.  (I can use "apps", right, or does the word belong to Apple now?)  :-)

---

