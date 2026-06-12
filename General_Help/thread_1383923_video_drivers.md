---
title: "video drivers"
date: 2010-01-17
forum: General Help
---

### Post by RFXCasey on 2010-01-17
Does the latest version of Ubuntu support the nvidia legacy drives 71.86.11 in particular? I need to get my Geforce2 GTS working and don't know if I should be using an older release of Ubu.

---

### Post by ubudog on 2010-01-17
Go to System>Administration>Hardware Drivers and select the recommended nvidia driver. Hope that helps. :D

---

### Post by RFXCasey on 2010-01-17
well ya, I know I can do that but I thought I heard that maybe the actual "correct" restricted drivers were no longer supported in the latest versions of Ubuntu and I would be stuck using the generic drivers which is what it winds up installing and gives no indication of a restricted driver that may be used under the (whatelse) restricted driver menu.

---

### Post by ubudog on 2010-01-17
You might need to install Hardy Heron (8.04) then.

---

### Post by lukeiamyourfather on 2010-01-17
The open source drivers should handle that card just fine. No point in using the official nVidia drivers for a card that's over a decade old. Typically the proprietary drivers are only necessary if an open source driver is not mature or unavailable. Cheers!

---

### Post by lidex on 2010-01-17
> **RFXCasey said:**
> Does the latest version of Ubuntu support the nvidia legacy drives 71.86.11 in particular? I need to get my Geforce2 GTS working and don't know if I should be using an older release of Ubu.

I kinda doubt it - it's not listed in the repositories for karmic. Version 71 is available in Jaunty however.

---

### Post by RFXCasey on 2010-01-17
Well the main problem is I can't get any videos, mame, or dosbox to go fullscreen and I am figuring it is these generic video driver. So hope someone can help me with that.

---

### Post by lukeiamyourfather on 2010-01-17
> **RFXCasey said:**
> Well the main problem is I can't get any videos, mame, or dosbox to go fullscreen and I am figuring it is these generic video driver. So hope someone can help me with that.

Well, them's the breaks as they say. Maybe its time to upgrade the hardware if you want to keep up with modern software. At some point its not longer logical or feasible to maintain support for legacy hardware, and I'd say a decade is getting up there. Cheers!

---

### Post by RFXCasey on 2010-01-17
> **lukeiamyourfather said:**
> Well, them's the breaks as they say. Maybe its time to upgrade the hardware if you want to keep up with modern software. At some point its not longer logical or feasible to maintain support for legacy hardware, and I'd say a decade is getting up there. Cheers!

Huh huh, well that's not this issue, as a matter of fact I happen to have several "modern computers" Like my little AMD Kuma 2.7 with  an ATI 4830 and 1.5 Tb of HDD. Or my x64 2.4Ghz that I currently have a Nvidia 6800 which ain't all that shabby neither. The fact is that I am using this old hardware in my mame cabinet and was using window but would really rather convert it to linux.

---

### Post by lukeiamyourfather on 2010-01-18
> **RFXCasey said:**
> Huh huh, well that's not this issue, as a matter of fact I happen to have several "modern computers" Like my little AMD Kuma 2.7 with  an ATI 4830 and 1.5 Tb of HDD. Or my x64 2.4Ghz that I currently have a Nvidia 6800 which ain't all that shabby neither. The fact is that I am using this old hardware in my mame cabinet and was using window but would really rather convert it to linux.

Then maybe try the 6800 card in your MAME setup? Don't know why you're getting huffy about it because its not meant to be offensive. Let me reword it, it will probably be easier to try newer hardware than to work out the bugs/limitations of the older hardware.

---

### Post by RFXCasey on 2010-01-18
No huffiness, peace, love, goodwill and all that. I just thought your comment was funny. I need that 6800 for my simulator I am making. The mame machine doesn't have to be that powerful to do it's job. I really don't care what Linux I use. I may try Debian. I just don't understand why I can't fullscreen. If you or anyone else knows how to solve my problem clue me in. I could try xfce or whatever it's called but I figure all that will do is free up some memory and don't think it will help me achieve fullscreen.

---

### Post by RFXCasey on 2010-01-21
Just wanted to put this out there for anyone having issues getting the restricted drives working for their pre 6800 Nvidia cards. Well, I can pretty much confirm that you will need to use 8.04.3 LTS (Hardy Heron)if you want any kind of decent video performance or at least 3d acceleration. Heron picked up my GeForce2 GTS right away an the performance difference in Mame was profound. That an the fact that I can actually run things at true fullscreen now including videos. As far as Mame not running in true full screen this may have been more of an issue of using xmame instead of sdlmame but regardless the overall graphical performance in everything is 100% better then with the generic drivers 9.10 was trying to use. Now if I was really geeky I guess I would try the exact same driver that heron installed under Jaunty. I had tried the Nvidia legacy drivers in 9.10 but that may have been a different version then what heron is using now I just haven't checked. I am thinking though it (the driver that is) may require some recompiling for Jaunty but I really don't know a lot about that. If anyone has any input on whether or not these old card are or can be supported in any way in 9.10 please chime in as I am sure some of us are curios. Oh and by the way, I can haz smile now :biggrin:

---

