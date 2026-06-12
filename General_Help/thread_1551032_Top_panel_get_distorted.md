---
title: "Top panel get distorted"
date: 2010-08-11
forum: General Help
---

### Post by thepriebe on 2010-08-11
Hello,

When my laptop (Asus X83VM) first boots up and Lucid (10.04) loads, my top panel on the right hand side where the power button, date, user name, volume control, mail icon, battery level, etc, is all 'garbly-gook.' By 'garbly-gook' I mean icons are over-lapping and missing. If I move the panel to a different location (right or left, but not bottom), the panel seems to reset and is no longer garbly-gook. 

Anyone have any ideas?

---

### Post by ricardisimo on 2010-08-12
Does it look anything like this? (see attachment, to the right, just above the arrow) This is happening regularly on my wife's and son's accounts, but never on mine.

To correct it, I have to right-click on the top panel, select Properties, and change the pixels up and back down for a sec. That resets the panel to where it is usable.

---

### Post by Vaphell on 2010-08-12
sometimes it's the network applet that causes that, at least that's what i experienced. If you switch to another account while logged in it won't start because there can be only 1 instance of it (first account has it) and the panel goes berserk. What's better - switch again to the first account, log out and other logged in accounts lose network. When first session goes down, so does the network applet. Since the other sessions failed to launch it at their initialization, they don't have it so no network.
That is a huge, outright unexplainable design flaw. They put the switch user option in the desktop ui, apparently for people to use it, but when you actually use it, you get a nasty glitch - it doesn't make any sense.

---

### Post by davidogg on 2010-08-12
> **ricardisimo said:**
> Does it look anything like this? (see attachment, to the right, just above the cursor) This is happening regularly on my wife's and son's accounts, but never on mine.

To correct it, I have to right-click on the top panel, select Properties, and change the pixels up and back down for a sec. That resets the panel to where it is usable.

I get that on my netbook, in 10.10-3 it seems to be fixed.

---

### Post by thepriebe on 2010-08-12
> **ricardisimo said:**
> Does it look anything like this? (see attachment, to the right, just above the cursor) This is happening regularly on my wife's and son's accounts, but never on mine.

To correct it, I have to right-click on the top panel, select Properties, and change the pixels up and back down for a sec. That resets the panel to where it is usable.


Yeah, that's exactly what I have to do too to fix it. Some days I get an over lapping user name. Sometimes other icons over lap. And it's only on the right side. The left always shows properly, along with the bottom.

---

### Post by Monkeystador on 2010-08-13
If got this problem too, but it occurs when enabling autostart for gnome-do.

---

### Post by ricardisimo on 2010-08-23
Has anyone filed a bug? Is gnome-do the common denominator? I installed it, but never use it.

---

