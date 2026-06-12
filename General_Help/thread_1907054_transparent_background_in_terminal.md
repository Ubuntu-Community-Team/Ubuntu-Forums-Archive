---
title: "transparent background in terminal"
date: 2012-01-10
forum: General Help
---

### Post by doktorOblivion on 2012-01-10
Once again, my background in my terminals is no longer transparent.  It always shows some grey-out pattern.  All other options, images, colors for background seem to work, but when I select transparent, nothing.

I did have a system crash a while back and then recovered my xfce desktop (they need to work on this, its worse then explorer, go figure), but this still remains the only thing not working.

Ideas?

---

### Post by imachavel on 2012-01-10
I don't know where the transparency back ground is, but all the other back ground sections work for me:

---

### Post by QIII on 2012-01-10
When you select transparent, is there a "slider" that allows you to select percent of transparency?

---

### Post by doktorOblivion on 2012-01-10
Yes, of course.  But it does not work for any position, still grey.

---

### Post by QIII on 2012-01-10
Are you using a compositor?

---

### Post by doktorOblivion on 2012-01-10
Here is an example, I have the profile change dialog pulled up for terminal session I use.  I can slide the transparency slider from none to max, nothing comes through.  I consider this a recent bug, though on earlier versions I have witnessed it as well.  I think it is a regression.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Using XFCE desktop, not One.

---

### Post by doktorOblivion on 2012-01-10
No.  Just the terminal profile properties, that is all.

I am wondering if there is something I can delete and restart xfce to get it back?  Actually just noticed its actually gnome terminal.

---

### Post by galerie on 2012-11-04
Just figure it out :D

you have to enable compositor under setting>appearance>window manager tweaks>compositor>enable display compositing.

this work for me :D

---

