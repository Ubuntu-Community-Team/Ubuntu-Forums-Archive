---
title: "iPhone - how to add photos?"
date: 2010-05-26
forum: General Help
---

### Post by windfix on 2010-05-26
How can I load photos ONTO the iphone using 10.4?  Lucid can clearly write to the iPhone, but my photos don't show up just by dragging them into the iPhone /Photos directory.

---

### Post by cmmckoy on 2010-05-27
Have you tried giving it the correct permissions?  Try SSH'ing into the phone, going to the correct directory, and using 'chmod 775 <imagename>' and possibly restarting/respringing your phone.

---

### Post by windfix on 2010-05-28
Thanks for the suggestion, I will try.  However, a workaround is to drop the photos into the /DCIM/100APPLE folder where the iPhone camera stores its pictures.  They show up on the "camera roll" without any further fussing.

From there you can use them as wallpaper, email them, etc. The thumbnail versions don't, however, get generated.

---

### Post by aabler on 2011-03-26
> **windfix said:**
> Thanks for the suggestion, I will try.  However, a workaround is to drop the photos into the /DCIM/100APPLE folder where the iPhone camera stores its pictures.  They show up on the "camera roll" without any further fussing.

From there you can use them as wallpaper, email them, etc. The thumbnail versions don't, however, get generated.

Using iPhone 4 w iOS4.0. Copying appropriately named (e.g. IMG_XXXX.JPG) files into /var/mobile/Media/DCIM/100APPLE and the thumbnail counterpart (e.g. IMG_XXXX.THM) into /var/mobile/Media/PhotoData/100APPLE doesn't seem to work (not showing up in camera roll on phone).  I've tried thumnails of 75X75 and 150X150. Suggestions anyone?
Oh yeah, and what are BTH, THL and THP files - also in the PhotoData/100APPLE section...

---

