---
title: "Crahsing gnome (x-server?) with gedit"
date: 2006-06-14
forum: General Help
---

### Post by Daywalker313 on 2006-06-14
Hi,
I found an - at least for me - reproducable way to crash gnome or even make xorg restart with gedit.
I'm not sure wheter it's a problem with my installation or if it works on all computers.

These are the steps:
```
cd ~
wget http://stuff.stgc.de/e_demo.html
gedit e_demo.html
```

I have line-wrapping disabled, html highlighting enabled and just need to scroll around a bit with either the keyboard or mouse to make it crash.
I'm running a fully patched LTS on amd64.

If this happens for you too, please also tell me where to report it, because gedit bugs are not reported via the launchpad, however, I'm not sure if this is actually a failure of gedit.

PS: I hope the location for this thread is not completly wrong, I didn't find a better category.

~Daywalker

---

