---
title: "How to adapt it to a new graphics env?"
date: 2010-10-17
forum: General Help
---

### Post by HiSiskin on 2010-10-17
I'd like to move my current hard drive, which is an old PATA IDE on an almost-dying BTO PC made in 2001, to a new machine using an IDE to SATA converter gadget.

The hard drive itself is relatively new and healthy, and of course, on which my loving Ubuntu lives.

The foreseeable problem is the incompatibility of the graphics hardware, which currently is a Matrox one, between the one current Ubuntu might expect and the one that would reside on a new machine.

Could we adapt it(Ubuntu) to a new machine after it boots on it(the new machine)?  If the answer is yes, then, how? The new machine is not decided yet so the new graphics can't be known currently.

Could Ubuntu do auto-adapting/adjusting for that issue?

---

### Post by Vaphell on 2010-10-17
once i had my work laptop fixed in similar way. HDD was moved to a recycled laptop with similar configuration, only thing required was 1 change in xorg.conf (gfx driver name). Now xorg can autodetect stuff so even that step wouldn't be necessary.

---

### Post by Schrute Farms on 2010-10-18
I found myself in a similar situation once.  In 9.10, I bought a new graphics card for my system.  I went from an ATI to Nvidia.  After the card install, all I got was a black screen with the cursor.  Everything seemed to be running OK, I just couldn't see.
Unfortunately, I can't help you fix the problem, just want to give you a heads up.  I couldn't run 10.04 with the ATI, which is why I got the Nvidia.  So I just did a new install.

---

### Post by efflandt on 2010-10-18
Does that Matrox use any special drivers or just default drivers?  It would be best to revert to default video drivers before the move, if possible.  Then you could use the default video until activating proprietary drivers.

I had no trouble booting a USB drive with nvidia driver installed, on a PC with legacy ATI, except that the system pointed to nvidia specific glx instead of mesa glx, which put a damper on 3D.  But from Schrute Farms it sounds like ATI proprietary drivers do not like nVidia.  Hopefully you could at least boot a (recovery) kernel to a text console if you need to remove something.

---

### Post by Yarui on 2010-10-18
I agree that changing to generic drivers would probably be a good decision, although even if you didn't do this before moving the drive, you could always boot into recovery mode and do it there.

I don't think anyone can really tell you for sure whether or not you would have any issues, it probably mostly depends on how different the hardware is and how lucky you are.  It sounds totally doable, but you won't really know until you try.  There is a good chance you will have some issues, but they will probably be manageable, just report back with your findings and hopefully someone can help you with any problems you might have.

EDIT:  I have had some issues with default video drivers on my current video card, so there is a chance that even if you change to default video drivers you won't get video right away.  If that happens, just boot into recovery mode like I already said and you can make the necessary changes.  I actually had to use recovery mode as part of my installation process with 10.10 because the default video drivers wouldn't run properly on my card.

---

### Post by HiSiskin on 2010-10-18
Thanks all the nice folks.

I love Yarui's easygoing posture of mind.
I surely would try to have my own one.

Thanks again.

---

