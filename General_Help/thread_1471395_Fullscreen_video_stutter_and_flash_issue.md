---
title: "Fullscreen video stutter and flash issue"
date: 2010-05-03
forum: General Help
---

### Post by sunrex on 2010-05-03
Hello,

I have a problem with my videos. Whenever I'm full screen it stutters/freezes for a few seconds and goes back to normal, repeat. This only happens when fullscreen and not when the window is maximized. I am using a internal graphics chipset, ATI SB700.. or something similar.

Also, my flash stopped working correctly a day ago. It was working fine before that, I can still play flash videos and everything - but I cant press any buttons on them. I use the flash in the ubuntu software center.

---

### Post by Taus on 2010-05-03
dunno about your fullscreen error but i think i can help wiv the flash bug.

seems like a lot of people has this flash issue with the 64bit version of ubuntu.. i posted it a few time on this board today try if it won't work for you as well:

i had the same problem... i noticed that i could work it around by holding down the right mousebutton on the flash object and then left click the flash button i wanted to click while still holding down the right mouse button.

i then found out i could completely fix it by doing this from the terminal:

sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this before the last line of text “export GDK_NATIVE_WINDOWS=1&#8243;, then save and restart the application that uses flash.

it worked for me  but i think it's only for 64 bit version of ubuntu. I hope it works for you as well..

cheers

---

### Post by sunrex on 2010-05-03
I'm also on 64 bit ubuntu, the flash bit worked like a charm - thank you!.

---

### Post by freetolio on 2010-07-09
Between this and disabling desktop effects, 32-bit flash works great on all my 64-bit Ubuntu 10.04 systems now.  Thank you.:p

---

