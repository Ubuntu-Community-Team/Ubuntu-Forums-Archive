---
title: "udev keyboard tool and MS Arc keyboard"
date: 2010-07-25
forum: General Help
---

### Post by mttolmie on 2010-07-25
First, is this the correct form for this?
I have wireless MS Arc keyboard running under 10.04 32 bit. Its arrow keys are too small for my fingers and I want to introduce something like a modifier with hjkl as bigger arrow keys. 
I looked at the udev keyboard tool located in /usr/share/doc/udev.
First problem: when I run l
/lib/udev/findkeyboards I get
USB keyboard: input/event, event3 and js0 
When I then query it answers Microsoft NanoTranceiver for the eventX and invalid argument for js0. In short nothing like the current mapping.
Anybody knows  how to get the mapping?

By the way, a similar but I belief older approach is in
[http://superuser.com/questions/96299/mapping-superhjkl-to-arrow-keys-under-x](http://superuser.com/questions/96299/mapping-superhjkl-to-arrow-keys-under-x) which works with a ~/.Xmodmap: do we have two complete mechanisms in place to do the same things?

---

