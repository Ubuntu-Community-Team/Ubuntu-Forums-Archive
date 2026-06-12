---
title: "1 inch blacked out section of screen"
date: 2011-03-22
forum: General Help
---

### Post by Reaper815 on 2011-03-22
Earlier today I was attempting to install XBMC, on the wiki I was directed to installing nvidia acceleration drivers, I also did that. Upon restarting my computer, i had about a 1 inch blacked out part of my screen that extended the entire length of the screen(so basically from the applications bar to the bottom of the screen. I attempted to remove the acceleration items but the problem still persists. When i move my mouse over the applications it pops up like in the picture, but other than that it remains blacked out

---

### Post by Mat11 on 2011-12-23
> **Reaper815 said:**
> Earlier today I was attempting to install XBMC, on the wiki I was directed to installing nvidia acceleration drivers, I also did that. Upon restarting my computer, i had about a 1 inch blacked out part of my screen that extended the entire length of the screen(so basically from the applications bar to the bottom of the screen. I attempted to remove the acceleration items but the problem still persists. When i move my mouse over the applications it pops up like in the picture, but other than that it remains blacked out

The same thing has happened to me as a Maverick user on a 64 86 machine.
If you find out the solution let me know.

Thanks Matt

---

### Post by saneearth on 2011-12-23
Since you still have the bar on the far left of your screen, it appears to me that it may just be that your Wallpaper is not "stretched" to fill the screen. When you installed the nVidia drivers, this may have caused the resolution to change, which changed how much screen your wallpaper occupied. Try changing wallpapers and if there is an option to "stretch" it do so. I haven't had this issue with 11.10 and realize there are less options than previously, so I am unsure exactly where you would do this. Just try merely changing the wallpaper from "Appearance" first and see what happens.

---

### Post by Mat11 on 2011-12-24
> **saneearth said:**
> Since you still have the bar on the far left of your screen, it appears to me that it may just be that your Wallpaper is not "stretched" to fill the screen. When you installed the nVidia drivers, this may have caused the resolution to change, which changed how much screen your wallpaper occupied. Try changing wallpapers and if there is an option to "stretch" it do so. I haven't had this issue with 11.10 and realize there are less options than previously, so I am unsure exactly where you would do this. Just try merely changing the wallpaper from "Appearance" first and see what happens.


 Correction from an earlier note to include :--

 After obtaining compiz fusion icon from the Ubuntu software centre i found that after ticking the indirect rending option in the list provided on the left top bar has helped somewhat.The blacked out area around the dock icons vanishes - immediately.But after the computer is turned off and on the blacked out area returns. However i did notice on the right it said compositing needs to be enabled ???
Wish i knew where to go from here ? I'm wondering if i've picked up an update that effects graphics and rendering ?
Have already tried to fiddle with compiz-setting-manager obtained from the synaptic package handler but have not spent enough time with it.
Think this is a bit of a game with graphics !

Good luck and Merry Xmas.

----------------------------------------------------------------------------------------------------------------

late Update:--

 Solved it on my computer-- found that for some reason an old driver that was enabled under additional drivers in System>Administration was the cause (basically i got rid of it).Then checked under System>Preferences>appearences that normal was checked-marked.Next i turned the comp off and on and all is now back to normal.

---

