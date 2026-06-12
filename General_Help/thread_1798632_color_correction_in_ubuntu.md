---
title: "color correction in ubuntu?"
date: 2011-07-06
forum: General Help
---

### Post by princeofnam on 2011-07-06
I have a laptop so i can't adjust contrast/brightness/color settings for my screen display.  Is there any such setting panel for Ubuntu?  On my other PC it was easy because nVidia's proprietry driver came with those options but I can't find anything for my integrated intel graphics card.

---

### Post by CatKiller on 2011-07-06
There's **xgamma**. You can adjust each of the red, green & blue channels and once you've found the settings that you like you can put one line in xorg.conf to have it applied each time you boot. 

It's also possible to load a colour profile should you have such a thing, but I can't remember exactly how I did that.

---

