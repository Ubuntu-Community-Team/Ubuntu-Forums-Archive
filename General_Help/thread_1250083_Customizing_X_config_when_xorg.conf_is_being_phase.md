---
title: "Customizing X config when xorg.conf is being phased out"
date: 2009-08-26
forum: General Help
---

### Post by darsu on 2009-08-26
/etc/X11/xorg.conf comes empty nowadays. This, so I gather, is due to its being deprecated in favor of automatic detection of devices.  The obvious question is: what do I do if this automatic configuration doesn't go right?

I have a misbehaving fresh installation on an old computer; some googling has suggested adjustment of the AccelMethod option as a fix, but where am I to make such adjustments in the new scheme of things?

---

### Post by CatKiller on 2009-08-26
You can still modify or create an xorg.conf, and for most things that will over-ride the automatic detection. I believe that the mouse section is the only one that doesn't still work. Everything else should be fine.

---

### Post by darsu on 2009-09-05
Thanks, it works. I also had trouble getting keyboard layout settings to stick, but that was settled in this way also.

---

### Post by Gen2ly on 2009-09-05
Just as a side-note xorg.conf probably won't be deprecated soon or possibly ever.  Automatic detection being nice and all people will probably like to do customizations in the future.

---

### Post by darsu on 2009-09-05
Roger that. I was wondering whether preserving xorg.conf as a configuration override is a permanent arrangement or if we're just in a period of transition.

---

### Post by bodhi.zazen on 2009-09-05
I believe we are in a period of transition. Some of the old edits I used to do to xorg.conf no longer work and some things are moving to hal (synaptics touch pads for example).

---

