---
title: "USB mouse freezes in kernel 0.24 generic"
date: 2012-05-13
forum: General Help
---

### Post by sirriffsalot on 2012-05-13
Heya!

Yesterday the annoying freezing of my mouse began in the 0.24 generic kernel a few moments after I log in, but if I go for the 0.23 lowlatency one which can be selected in the grub selection menu under "Previous Linux Versions", there are no problems what so ever with my USB devices. If I do a ```
dmesg
``` when the mouse has frozen it says "usb_set_interface_failed" accumulatively in accord with when I move or click the mouse... Any ideas on this annoying issue? I'm running on 12.04, so I suppose this is pretty new..

Thanks for your time!

---

### Post by jonnyboysmithy on 2012-05-13
I assume you mean kernel 3.2.0-24-generic?
Can you give us the output of ```
uname -r
``` just to be sure

Have you tested with other mice? (or mouses whatever..:))
Maybe this is a bug.

---

### Post by sirriffsalot on 2012-05-13
Hey!

Yes, I meant just that, I just couldn't be bothered to find out what it was named exactly. But that's the output ;)

Yes, I've tested with ps2 mouses in 0-24-generic and it works fine... So this is surely a bug!

---

### Post by jonnyboysmithy on 2012-05-13
Then lets report it! I wonder if it will get a high priority...

---

### Post by sirriffsalot on 2012-05-18
Now it isn't happening anymore, unless I hook-up my mustang amplifier or do something "USB-Configuring"... How would I approach reporting this bug?

---

