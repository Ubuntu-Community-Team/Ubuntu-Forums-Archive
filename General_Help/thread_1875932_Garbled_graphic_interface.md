---
title: "Garbled graphic interface"
date: 2011-11-05
forum: General Help
---

### Post by Mr.Batch on 2011-11-05
Brand new to Ubuntu, and have been enjoying the performance after replacing XP and moving my files to the new OS.  After using a few apps, some of the graphics/text will appear to break up.  I first noticed the problem with the labels that appear for the launcher icons when you hover over them.  The text and backing graphic for the labels would appear scrambled, as if the lines of the bitmap were randomly moved to one side or another.  I then noticed that the search screen for the dash app would also appear scrambled.  The effect goes away when you restart, but comes back after using a few apps.  I will try to include a screenshot soon with an example of the problem as soon as I can.

The only similar issues I can find on the web seem to be happening with Dell computers.  Is this a compatibility issue with Dell graphics drivers?  The system info lists the graphics driver as "unknown"


Any help would be appreciated.

Edit:  Following the advice of another forum, I changed a kernel function in grub 2 so that the unity bar is 2D instead of 3D.  Works perfectly now, although I miss the old bar.  Maybe updates will make it work with my old Dell E310 graphics card, but for now it's fine.

---

### Post by slickh20 on 2011-12-04
I am having a similar issue I believe, the new bar looks great but the popup labels and the text in the program menus is all garbled and hard to read.  

anyone else have this issue?  

if not how did you get the 3d to 2d?

---

### Post by collisionystm on 2011-12-04
do you have an ATI / AMD video card?

That is generally a problem related to them

---

### Post by bluexrider on 2011-12-04
The OP is 4 weeks old. Isnt usually the E310 have Nvidia.

> **collisionystm said:**
> do you have an ATI / AMD video card?

That is generally a problem related to them

---

### Post by slickh20 on 2011-12-04
standard on board intel graphics, pretty basic system.

---

### Post by oldtimer7777 on 2011-12-04
> **slickh20 said:**
> standard on board intel graphics, pretty basic system.

You can switch to 2d in 11.10 by clicking the little gear icon in LightDM login screen and selecting your session to be 2d.

---

