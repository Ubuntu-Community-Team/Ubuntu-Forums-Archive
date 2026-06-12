---
title: "weird blinking problem"
date: 2009-08-09
forum: General Help
---

### Post by SergeantBuck on 2009-08-09
So I just installed ubuntu 9.04, and I'm a total n00b.

My friend was helping me set it all up, and everything was fine.

But then one time when I logged in to my account the two taskbars at the top and bottom of the desktop kept blinking.  Any windows I opened also blinked.

When I tried switching over to a guest account, however, the blinking stopped and ubuntu was fine.

I assume this must be some kind of setting issue that I've created on my account.
Does anyone know how to fix it?

---

### Post by P4man on 2009-08-09
are you using compiz "desktop effects" ? If so, or if you are unsure, go to system > preferences > appearance > visual effects  and set them to "none".
If that cures it, at least we know its a compiz problem, and we can look further in to it.

---

### Post by zkriesse on 2009-08-09
That's prob what it was...just a setting that you changed my man

---

### Post by SergeantBuck on 2009-08-10
yeah it was the Window Decoration effect in Compiz.
idk why that messed it up, I think it was on the whole time.

Anyhow, thanks a bunch for the help, guys!

---

### Post by P4man on 2009-08-11
the windows decorator plugin should actually be turned on. Though it sounds as if you had 2 windows decorators active, which would plausibly explain flickering I imagine.

In compiz, go to windows decoration, and in the command line, make sure it says: 

gtk-window-decorator --replace

then turn the plugin on.

---

