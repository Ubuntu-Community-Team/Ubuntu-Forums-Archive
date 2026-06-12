---
title: "ICC profiles where to apply?"
date: 2010-08-13
forum: General Help
---

### Post by ravinderw on 2010-08-13
Hello All,
 
I'm running Ubuntu 10.04 and have managed to profile the monitor and install the generated icc so that the monitor uses it.
 
My question now is do I need to go to every application and configure them to use the profile or is having the monitor using the profile enough?
 
For example, do I need to go to gimp and tell it to use the profile as well?
 
thanks.

---

### Post by pekarna on 2011-04-15
Hi,

I set the ICC profile for my flawed monitor (LP2475w) using gnome-color-management which I installed, and nothing happend. In GIMP, I had to go to Preferences -> Color Management -> Monitor Profile. Then the image was what I'd call +- realistic colors. But Gnome and all other apps were still oversaturated.

Update:
Actually, setting the profile in gnome-colors-manager had effect, but for some reason, only on dark colors, not on the oversaturated red (my problem with HP LP2475w). In GIMP, the ICC profile had the effect I'd like to see on whole desktop.

Does anyone know how to achive that?

---

