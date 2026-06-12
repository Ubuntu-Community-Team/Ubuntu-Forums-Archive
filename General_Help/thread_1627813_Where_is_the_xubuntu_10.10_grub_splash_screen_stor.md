---
title: "Where is the xubuntu 10.10 grub splash screen stored?"
date: 2010-11-21
forum: General Help
---

### Post by Willard on 2010-11-21
Hi folks,

I am running xubuntu 10.10 and I am looking into theming my GDM and my xfce in a consistent way. I find the splash screen that I see while booting ("xubuntu [mouse]", in white, on a pitch-black background) to be very appealing.

I tried looking for the image on the web, but could not find it anywhere. Then I tried figuring out where on my machine the image is located, but after almost 2 hours of searching, I could not find it. The closest hint I got was in /etc/grub.d/05_debian , which mentions

/usr/share/images/desktop-base/moreblue-orbit-grub.png

but this image does not exist in my machine (in fact, /usr/share/images does not exist).

Where is the xubuntu 10.10 grub splash screen stored?

(if you need me to, I can photograph the splash screen as I am booting, although that will be quite awkward...)

Thanks in advance!
-W.

p.s.: If you happen to know how to conveniently change the GDM login theme in xubuntu 10.10 as well, I would appreciate some pointers.

---

### Post by Willard on 2010-11-22
*bump*

(if this thread is in the wrong forum, I'll be happy to move it / have it moved)

---

### Post by Happy Frog on 2011-03-11
It's in /lib/plymouth/themes/xubuntu-logo/

As for the login screen, I found it simple to just change the default images. The horrible retina scarring background is /usr/share/xfce4/backdrops/xubuntu-bluebird-notext.png and the default icon is /usr/share/pixmaps/xubuntu-logo.png

---

