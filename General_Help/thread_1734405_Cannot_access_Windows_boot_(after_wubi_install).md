---
title: "Cannot access Windows boot (after wubi install)"
date: 2011-04-20
forum: General Help
---

### Post by a01chtra on 2011-04-20
Thanks for reading this, and feel free to move to another more suitable place if I have posted in error in general help -  couldn't find the startup/dualboot section and I'm too panicky to hunt.

Essentially, I installed Ubuntu Maverick as a dual boot with Windows 7 on one (massive) harddrive. I recently decided to set Ubuntu as the default OS, and was advised to do so in Windows since I had apparently installed with Wubi rather than as a full install (the Windows loader came up each time the computer booted).

So I changed the default OS in My Computer --> Advanced System Settings in Windows 7, and set the time for the loader to appear to 1 second (in case I needed it). In retrospect, I wish I had left it at the default 10 seconds because the loader just doesn't appear any more. I do sometimes need Windows for specific programs (SONAR8 etc.) which would be an unbelievable hassle in Wine.

Please help me bring the loader back! Or even any way at all of just getting back into that version of Windows - would the original install disc help? :confused:

Thanks again for reading this and all help welcome!
a01chtra

p.s. Hedgewars rocks

---

### Post by mike555 on 2011-04-20
Can't you push the Shift key and have grub show up ? you will need to time it right.

---

### Post by Mark Phelps on 2011-04-20
Since you're using the Windows boot loader, I would try repeatedly pushing F8 to see if you can force it into displaying the OS selection menu.

---

### Post by a01chtra on 2011-04-20
Hey guys, thanks for the advice - I tried hammering the "up" key throughout boot loading and it WORKED, wubi was still there, it just didn't show. I changed the timer to 4 seconds to avoid such panic in future.

YAY BOTH OSs WORKING
:guitar:

a01chtra

---

