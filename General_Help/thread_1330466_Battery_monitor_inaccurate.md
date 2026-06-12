---
title: "Battery monitor inaccurate"
date: 2009-11-18
forum: General Help
---

### Post by snakeman21 on 2009-11-18
I recently upgraded my wife's computer (and mine) to Karmic Koala.  My battery monitor seems to work fine, but hers is... screwy.  Last night, it told her that she had five minutes of power remaining.  She continued to use the computer for 45 minutes, all the while being warned that the computer was about to hibernate.  Is there any way to fix this?  

A friend told me that I should disable all the power management setting, and let the laptop die (preventing it from hibernating).  Then, I should charge it fully without turning it on until it's done.  The only problem with this is that Karmic doesn't seem to let you disable all the power options.

Any suggestions?

---

### Post by billyboy1978 on 2009-11-18
Upload and drain your battery a couple of times. I did that, and it worked well.

Otherwise you can always kill power-manager
$ killall gnome-power-manager

---

