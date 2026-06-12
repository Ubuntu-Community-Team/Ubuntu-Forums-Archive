---
title: "problem with trident cyber 9525 driver"
date: 2006-04-28
forum: General Help
---

### Post by scrimp212 on 2006-04-28
I have seen threads about this problem with this specific video card and driver. I am completely lost as to what to do and would like some help to fix this problem. Thanks!

ps. Here is a screenshot of the desktop with the lines at the bottom of the page

update: 4/30/2006
I have fixed my problem with the fuzzy blurry lines at the bottom of the page. All I did was edit my xorg.conf file in the /etc directory and changed the line

driver "trident" ==> driver "vesa" and it worked!! no more lines woohoo:D

---

### Post by scrimp212 on 2006-04-30
bump

---

### Post by Kouki on 2006-11-07
Hi,

I to have this problem, just trying to solve it as you did, but I can't find my xorg.conf file.  I've looked in the etc folder and also tried searching my computer for it, yet it's not there.

I've checked synaptic package manager and according to this, the xorg trident driver is installed already.

Any ideas where my xorg.conf file is?

---

### Post by scrimp212 on 2006-11-07
im sorry I didnt provide the entire path. I think its /etc/X11/xorg.conf. Check that and let me know if that helps

---

### Post by Kouki on 2006-11-08
Ah, thanks, I've found it.  Now the interesting thing, is that if I browse to the file and right click to open using text editor, it opens fine and I can see all the text but can't edit it as it's read only because I don't have root privilages.

However,

sudo gedit /etc/x11/xorg.conf
and
sudo nano /etc/x11/xorg.conf

both open the file, but there is no text.  Very strange.

I'll try logging in as root and opening the file by browsing to it, then editing it that way if allowed.

---

### Post by Kouki on 2006-11-08
Right, my laptop touch pad doesn't work when I log in as root.  Which makes things difficult!

I'll try plugging a normal mouse in.

---

### Post by xmastree on 2007-01-28
> **Kouki said:**
> 
However,

sudo gedit /etc/**[COLOR="Red"]x[/COLOR]**11/xorg.conf
and
sudo nano /etc/[COLOR="Red"]**x**[/COLOR]11/xorg.conf

both open the file, but there is no text.  Very strange.

This may be way too late, but that should be a capital X in there. X11 is not the same as x11 in linux.

---

