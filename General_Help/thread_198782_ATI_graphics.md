---
title: "ATI graphics"
date: 2006-06-17
forum: General Help
---

### Post by DoctorMO on 2006-06-17
I've followed the wiki guide for getting the non free ati drivers, they are all installed and as far as I can tell I've run everything required.

when I run the last test to get the glx info I get back mesa instead of ati so it doesn't look like it's worked but there arn't any instructions on what to do in the wiki when it fails. (you know things to check ect)

---

### Post by scxtt on 2006-06-17
i've only noticed this problem when i've set xorg.conf to use fglrx and there was a problem loading the kernel module [i always build it using the directions in my sig] ... for the most part i always have fglrx listed for fglrxinfo, but once when i tried to use 8.25.* the build of the module failed (i wasn't paying close attn when it was building) and on the subsequent reboot mesa was listed ... [ that problem was the result of some Xorg 7 + 8.25.* incompatibility ] ...

---

### Post by stiankarlsen on 2006-06-17
use easyubuntu (google it), install the ati driver, change the the driver in xorg.conf to fglrx, reboot, and you're done.

---

### Post by DoctorMO on 2006-06-17
*sigh* looks like I've bought a compleat dud of a card, it's an ATI Radion 7000 and for some reason the ati fglrx driver doesn't support it :-(

What do I do now? throw it away and start again?

---

### Post by scxtt on 2006-06-17
yikes, aren't those one of the 1st Radeon cards made? ...

---

### Post by DoctorMO on 2006-06-17
But it's brand new! I thought I was getting an nvidia card, I know how to deal with those. damn it.

---

### Post by scxtt on 2006-06-17
the [brochure](http://www.ati.com/products/brochures/R7000Brochure.pdf) is from 2002, i think it's a bit outdated (in the sense you're not gonna get modern 3D accel support for it) ... even if you could, it's still an older (and not to powerful) card ... how much did you pay for it (if you don't mind me asking)?

---

### Post by DoctorMO on 2006-06-17
£16.95 from aria.co.uk

---

### Post by scxtt on 2006-06-17
what's that, about $32 USD? -- don't think you're gonna get much performance outta that ...

---

