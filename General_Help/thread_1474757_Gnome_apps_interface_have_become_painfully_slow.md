---
title: "Gnome apps interface have become painfully slow"
date: 2010-05-06
forum: General Help
---

### Post by drBouvierLeduc on 2010-05-06
[edit] see post below

Hi,

Since I switched to lucid  (clean install), the interface has become very slow, unresponsive. I had no such problem in  karmic. 
Switching from one window to another, displaying menus, browsing files, resizing windows etc... take ages to display.

Now what is strange, is that this problem _only affects native gnome applications_.
For instance Scribus or Blender run very smoothly, whereas Nautilus, Rhythmbox, Gimp or Inkscape, to name a few, suffer from those horrible lags.

I'm pretty sure it's not a driver problem, I'm using the latest nvidia-current drivers, and I tried everything : disabling compiz, disabling metacity compositing, using nouveau, using latest kernels, using xorg server 1.8... No change.

So I know the problem only affects native gnome apps, but now how can I find which package causes this mess ?
I just installed a few repos to have some recent graphic apps (gimp, inkscape, openshot, scribus... that's it), but I can't see in what way they could have messed with my system.

Well, any hint will be much appreciated, as at this moment my ubuntu is pretty much unusable... sigh...

---

### Post by drBouvierLeduc on 2010-05-06
Ok, this was much ado about nothing after all...
This mess was caused by a faulty libcairo2 package in a repo I added to  my software sources list (the gimp-dev one).
I switched back to ubuntu's default package and everything's fine now.

---

