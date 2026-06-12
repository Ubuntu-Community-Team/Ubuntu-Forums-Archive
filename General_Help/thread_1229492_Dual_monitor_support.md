---
title: "Dual monitor support?"
date: 2009-08-02
forum: General Help
---

### Post by virtual_pkh on 2009-08-02
I'm a very new Ubuntu 9.04 user.  I've gone that way since a recent WinXP update screwed things royally, and for me it was a real Basil Fawlty moment - you know, when he finally thrashed his car to bits with a branch when it failed on him.   Metaphorically that's what I did to XP, and because everyone and his dog was recommending Ubuntu as a "you can do anything in Ubuntu that you can in Windows" solution... here I am.

Well, the install went pretty well and I even (accidentally*) managed to get my system to dual boot for those things that Wine really won't run.   (* a long story, maybe another time)

And I've got to say that so far the experience hasn't been too bad.  Sure, the Ubuntu community view of a "simple" installation is very very different to a M$ view (can't remember the last time I needed to manually edit a config file in XP) but I'll let you off. Kind of.

But the thing that really seems to have stuffed me is dual monitor support.  I've an ATI Radeon 9550 card and I'm pretty sure I'm using the "out of the box" non-ATI driver because the one on the ATI website won't install.

I've an LG 1280x1024 digital connection as my primary monitor, and a Samsung 1024x768 VGA connection as my secondary.

Ubuntu recognises the two monitors, and kind of fits my desktop across both... but it's very broken.  The primary monitor has a 1024x768 "windows" in which everything's fine, but outside of this, bits of windows are left behind as you move them, etc.  The whole of the secondary monitor is like that.

Any clues on how I can resolve this?  

Thanks
Paul H

---

### Post by MaxIBoy on 2009-08-02
ATI's latest drivers have dropped support for your card. The latest version of the drivers which work with the Radeon 9550 are version 9.3 of the Catalyst drivers (version 9.7 is the latest.) Also, version 9.3 doesn't support the latest X-server (a critical component of a graphical Linux environment,) and it would be a major pain to install an old X-server on Ubuntu 9.04.

I know it kinda sucks, but the easiest way to get full acceleration on your card will be to downgrade (read: reinstall completely) to Ubuntu 8.10 and then install the older drivers. It's simply a matter of ATI being too quck to depreciate old hardware.

---

### Post by virtual_pkh on 2009-08-02
Thanks MaxIBoy, you're right, it kinda sucks.  One of the key plus points for Linux was the oft-repeated line about (I'm paraphrasing here) open source, huge community, problems often solved before you know you've got 'em, etc.  Seems a little different since I jumped over the fence.

I don't much like the idea of downgrading, and I don't much like the idea of going back to XP full time, so I might just invest in a new card... but I think I'll do a bit more research on that before I commit to any £££.

Appreciate the reply and sorry for the moan!

Paul H

---

### Post by MaxIBoy on 2009-08-02
Interesting you should mention that-- the problem is with hardware being depreciated in ATI's proprietary (closed-source) drivers. The open-source drivers for this hardware are not being depreciated (and never will be) because they're not bundled with the drivers for recent hardware, so there's no chance of them "dragging down the boat." In fact, the open-source drivers for the TDFX Voodoo3 are still recieving updates! And since ATI recently released the full specs for the R300 chips (including the chipset of the Radeon 9550,) you can expect to see the open-source drivers become on-par or better than the closed-source ones soon, at least on that hardware. 

But that day isn't here yet, and the 9550 is an ancient card anyway. You might just want to buy a new card and use ATI's latest drivers. On the other hand, as far as I know it was only available for the AGP slot, which probably means you have an AGP motherboard, which means you're looking at replacing far more than just only the graphics card (unless you want to settle for a less-ancient-but-still-not-new card. I have an old Radeon HD 2400 pro I'd be willling to let go of cheap. ;) )

---

### Post by rogblake on 2009-08-02
Another thing to consider if you are going to replace your video card is that historically Nvidia's binary closed-source drivers have been less troublesome than ATI's.

I have Ubuntu 9.04 running on a 2003-vintage Dell laptop with Nvidia GeForce 4 video and had no problems loading up the binary driver. So if you want something that "just works," Nvidia may be the way to go.

---

### Post by virtual_pkh on 2009-08-02
Quote: "...nvidia may be the way to go"

You may be right.  Part of the reason I "went ubuntu" on my main desktop machine was because I'd just gone through a flawless install on my ancient Tosh M200 Portege tablet PC (including nvidia gfx).  It really was an unexpectedly easy install, everything worked direct from the CD update.

Yep, AGP it is... I don't really want to replace the rest of the dektop as it just works. Is there a particular or recommended nvidia AGP card that'll work dual head under ubuntu?

Appreciate the comments.  This really is my first experience of (any) Linux, although my computer experience as a user & programmer goes all the way back to CP/M, PET and a home-built Acorn Atom!!

Paul H

---

### Post by bpalone on 2009-08-02
I don't know if this model is even still available, but I use a cheap Jaton 3D Force MX4000 Twin card that does fine.  It uses the nVidia GeForce MX4000 chipset.  I just had to install the NVidia drivers and set the monitors up.

Hope that helps you a bit.  I doubt this card is still available new, as it is a few years old now.

---

