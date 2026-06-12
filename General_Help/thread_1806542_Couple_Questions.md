---
title: "Couple Questions"
date: 2011-07-17
forum: General Help
---

### Post by cclloyd9785 on 2011-07-17
1.  What do I set the fonts to in 11.04 to make them as close to windows as possible? (I installed the Windows fonts and Calibri, and Tahoma).

2.  It seems that when I enable restricted drivers for my ATI Radeon Mobility 3100, the bootscreen doesn't boot in full resolution, and it SOMETIMES lags a bit...

---

### Post by xellink on 2011-07-17
> **cclloyd9785 said:**
> 1. What do I set the fonts to in 11.04 to make them as close to windows as possible? (I installed the Windows fonts and Calibri, and Tahoma).
 
Install the windows version of the fonts if you want. Also, if you use wine to run M$ office, u might need to delete some fonts in the wine folder.
 
> 2. It seems that when I enable restricted drivers for my ATI Radeon Mobility 3100, the bootscreen doesn't boot in full resolution, and it SOMETIMES lags a bit...
 
[http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/](http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/) 
 
There is a script there that solves your problem. Note that the fix for 10.10 is different from 11.04.

---

### Post by flipper T on 2011-07-17
2. install startup manager & change splash resolution

its in ubuntu software center

---

### Post by cclloyd9785 on 2011-07-17
Startup manager doesn't work as it doesnt have my resolution.  I have 1366x768 and it only has 5:4 resolutions up to 1024x768.

---

### Post by xellink on 2011-07-17
> **cclloyd9785 said:**
> Startup manager doesn't work as it doesnt have my resolution. I have 1366x768 and it only has 5:4 resolutions up to 1024x768.
 
1024x768 is probably a good choice, it doesn't make ur screen look that ugly.

---

### Post by wildmanne39 on 2011-07-17
Hi, for this problem here is a link that usually helps with that.
> it SOMETIMES lags a bit... 
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by cclloyd9785 on 2011-07-17
Still, right now with it disabled it displays in 1366x768.  There isn't any way I could keep it that way?

---

### Post by wildmanne39 on 2011-07-17
> **cclloyd9785 said:**
> Still, right now with it disabled it displays in 1366x768.  There isn't any way I could keep it that way?Hi, is just the boot screen resolution that you want to change?

---

### Post by xellink on 2011-07-17
> **cclloyd9785 said:**
> Still, right now with it disabled it displays in 1366x768. There isn't any way I could keep it that way?
 
You can try manually editing the files. The link i gave you actually explains what the script does, i.e. install uvesafb etc., but anything more than 1024x768 *might* not work. Worth a try, if you are feeling adventurous.
 
From what I experienced, 1024x768 is safe and not too bad, considering the benefits you get from the propriety driver. Otherwise, you'll just have to live without the propriety driver.

---

