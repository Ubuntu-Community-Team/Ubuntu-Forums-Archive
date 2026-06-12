---
title: "what's the problem with gvim?"
date: 2010-03-14
forum: General Help
---

### Post by engine on 2010-03-14
Finishing off an install manually after putting 9.10 on a new PC ... sorted out the "black desktop" problem thanks to the forum, so next question is "what is gvim trying to tell me?"
> (gvim:2610): GLib-WARNING **: g_set_prgname() called multiple times
** (gvim:2610): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

Advice and enlightenment gratefully received.

---

### Post by km0r3 on 2010-03-14
I suspect the reason you're asking this is because gVim is not more starting anymore?

> (gvim:2610): GLib-WARNING **: g_set_prgname() called multiple timesAccording to the [documentation]("http://library.gnome.org/devel/glib/stable/glib-Miscellaneous-Utility-Functions.html#g-get-prgname") this can be called only once, and here it is called multiple times.> ** (gvim:2610): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed                      This is a known bug. I found a patch [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545168"). Otherwise subscribe to any of [these bug reports]("https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188").

Looks like this issue is fixed in Lucid. :)

EDIT: If you want some advice: For software specific problems querying launchpad.net is never a bad idea. It's the "bug tracking tool" of Ubuntu and it's very probable that your bug was already reported before. :)

---

### Post by engine on 2010-03-16
Thanks for the explanation, though I'm not the type of user who enjoys bug-hunting ... GVim is working fine if I start it with a launcher, unless that method is simply hiding the error message as something [this type of user] doesn't need to bother his pretty little head with ;-}

I will take a look at the bug-report you mention, though, just to educate myself.

---

### Post by km0r3 on 2010-03-16
> **engine said:**
> Thanks for the explanation, though I'm not the type of user who enjoys bug-hunting ... GVim is working fine if I start it with a launcher, unless that method is simply hiding the error message as something [this type of user] doesn't need to bother his pretty little head with ;-}

I will take a look at the bug-report you mention, though, just to educate myself.
If you need any help please don't hesitate to ask. :)

Well, as said in Lucid this bug seems to be fixed.

---

### Post by jcbrown on 2010-04-19
> **engine said:**
> Thanks for the explanation, though I'm not the type of user who enjoys bug-hunting ... GVim is working fine if I start it with a launcher, unless that method is simply hiding the error message as something [this type of user] doesn't need to bother his pretty little head with ;-}

I will take a look at the bug-report you mention, though, just to educate myself.
[FONT=Calibri][SIZE=3]If you are someone who likes bug  hunting, then you are not just alone here. At least not in this page!  Glad to know Gvim is working fine. The patch above is effective against  the bug, anyway![/SIZE][/FONT]

---

