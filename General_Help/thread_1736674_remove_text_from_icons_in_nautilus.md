---
title: "remove text from icons in nautilus"
date: 2011-04-22
forum: General Help
---

### Post by nixIT on 2011-04-22
Hey all,

Installed 10.10 a couple weeks ago on my machine, and for the life of me, I can't find out where/how to remove the text from the toolbar icons in Nautilus.

There used to be an option under "Change Desktop Background", but it's no longer there.  I checked gconf-editor and can't find an entry under metacity.

Any idea how to remove the text next to the toolbar icons in Gnome (nautilus) in Ubuntu 10.10?

--nixIT

---

### Post by stinkeye on 2011-04-22
I think it's here but I can't test as 
I'm using Nautilus Elementary and the setting doesn't work with it.
```
gconf-editor /desktop/gnome/interface/toolbar_style
```
and change the value to "icons" .

---

### Post by nixIT on 2011-04-22
> **stinkeye said:**
> I think it's here but I can't test as 
I'm using Nautilus Elementary and the setting doesn't work with it.
```
gconf-editor /desktop/gnome/interface/toolbar_style
```
and change the value to "icons" .

That was it, thanks!!!

--nixIT

---

