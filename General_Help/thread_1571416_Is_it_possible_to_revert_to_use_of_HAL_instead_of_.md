---
title: "Is it possible to revert to use of HAL instead of udev?"
date: 2010-09-09
forum: General Help
---

### Post by lightstream on 2010-09-09
Hi, I have a Logitech marble mouse (trackball, [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)) which works great under HAL in Ubuntu 9.10.

For me it is simply not as usable without HAL, because it doesn't appear to be possible to have a button assigned to more than one thing. 

With HAL, you can click the back button on the trackball to go 'back', e.g. in Firefox, Nautilus, or you can hold down the same button to use vertical and horizontal scrolling with the ball (as opposed to the normal mouse movement when the button is not held down). You can also get a 'middle mouse' press by clicking both left and right buttons at once.

Can someone please help me restore HAL to the boot process so I can regain this functionality? Or is it not possible?

It would be just as good if I could get this same functionality without HAL, but I don't see how that can be done using xorg.conf.

Thanks in advance for any help.

---

### Post by lightstream on 2010-09-09
OK I just realised that HAL was setting the exact same options as xorg.conf, but using its own XML file (/etc/hal/fdi/policy/mouse-wheel.fdi).

Sheesh, there you go, that's what comes from copying & pasting from the web without paying attention to what you're copying.

The HAL .fdi file merely had the Emulate3Buttons option set to true, and it's this option which makes the left & right buttons when pressed simultaneously emulate the middle aka 3rd button. 

Seems pretty obvious now I noticed it! This is the usual setting for xorg.conf, but for some reason the ubuntu community documentation I linked to in my first post was setting this to false. Change that, and yes my marble mouse now works just the same but now without HAL woohoo!!

Incidentally it works much better with the native X driver than it does using Logitech's own driver (which is only available for Losedows anyway)

---

