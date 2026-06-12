---
title: "Compiz Config has disabled my xmodmap"
date: 2009-07-18
forum: General Help
---

### Post by Richardcavell on 2009-07-18
Hi,

I normally have a couple of xmodmap commands in my startup applications, to map my keyboard keys as pointer buttons:

xmodmap -e "keysym Super_R = Pointer_Button2"
xmodmap -e "keysym KP_Enter = Pointer_Button3"

I went fiddling with Compiz Config Settings Manager, and now they don't work. I can't figure out what I've done. How can I fix it?  By the way, I also have another xmodmap that maps a key to the control modifier, and that is not affected.  xev shows that the correct keysyms (Pointer_Buttonx) are being generated, but somehow X11 isn't responding to them.

Richard

---

### Post by Richardcavell on 2009-07-18
Hi, everyone.  I found the answer and I'll put it here in case someone Googles this later. It wasn't compiz-config that disabled my key-to-pointer-button mappings. I had turned off all Assistive Technologies. Mouse Keys must remain turned on for xmodmap to be able to generate pointer button presses.

Richard

---

