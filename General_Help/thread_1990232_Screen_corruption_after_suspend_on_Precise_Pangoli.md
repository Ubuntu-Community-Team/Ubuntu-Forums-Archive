---
title: "Screen corruption after suspend on Precise Pangolin"
date: 2012-05-29
forum: General Help
---

### Post by DadsArmy on 2012-05-29
After upgrading to 12.04, Precise Pangolin, my screen is corrupted after waking up from suspend (see attachment for a photo of it). I can still move the arrow in the top left rectangle (the photo is mirrored) and use keyboard commands there (although I can't see most of what I'm doing).

Any ideas how to fix this?

Thanks in advance,
Jelle

---

### Post by DadsArmy on 2012-07-19
A few kernel updates further, but still the same problem... :(

---

### Post by O2Blevel on 2012-07-19
I experience something similar, my corruption occurs on the top bar and the launcher but it disappears when I click the screen. I'm using an nvidia driver currently. This didn't happen when I was using the nouveau driver but the performance of that driver I found  lacking and it also created problems with compiz. Maybe try upgrading your video driver.

---

### Post by DadsArmy on 2012-07-20
Thanks for your reply, O2Blevel, I tried with both enabling and disabling the ATI/AMD proprietary FGLRX driver, but that didn't change anything. I have found a workaround though, since changing the resolution restores the screen in my case.

I've set two, custom keyboard shortcut for changing the screen resolution ("xrandr -s 0" and "xrandr -s 1" - 0 corresponds to my native resolution). Now when I resume after suspending, I first enter my password blindly (the dialog is not in the visible range) and then use the two shortcuts to change the resolution, and change it back.

Not the most elegant solution, but it's faster than rebooting...

---

### Post by DadsArmy on 2012-12-10
Somehow I can't delete a post, is this possible at all?

---

