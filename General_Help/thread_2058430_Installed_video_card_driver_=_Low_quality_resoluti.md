---
title: "Installed video card driver = Low quality resolution"
date: 2012-09-15
forum: General Help
---

### Post by TheHolyTape on 2012-09-15
Hey, I'm new into using Ubuntu and I'm having a screen resolution issue. I recently installed Ubuntu and so when I opened it up for the first time the whole screen the filled with display. The picture was sharp and videos on 1080p looked great! However, that was before I installed my video card driver (which was installed through automatic software that found the drivers through Ubuntu). My GPU is an ***ASUS 6770*** and here is a link to the product from the ASUS website: [http://www.asus.com/Graphics_Cards/AMD_Series/EAH6770_DC2DI1GD5/](http://www.asus.com/Graphics_Cards/AMD_Series/EAH6770_DC2DI1GD5/) . To my knowledge, I am pretty sure the GPU can give off a better display.


So once Ubuntu found the drivers I needed, it installed them, and then restarted the computer. When the computer restarted, the screen did not fill the entire monitor. Instead the display gave off a smaller display with black bars around it. Then the text looked rather choppy. I tested out the video display by going and trying 1080p YouTube videos, but I noticed they were a little choppy as well...

At this point I don't know what's wrong...

Some help please??? :D

---

### Post by dcstar on 2012-09-16
> **TheHolyTape said:**
> Hey, I'm new into using Ubuntu and I'm having a screen resolution issue. I recently installed Ubuntu and so when I opened it up for the first time the whole screen the filled with display. The picture was sharp and videos on 1080p looked great! However, that was before I installed my video card driver (which was installed through automatic software that found the drivers through Ubuntu). My GPU is an ***ASUS 6770*** and here is a link to the product from the ASUS website: [http://www.asus.com/Graphics_Cards/AMD_Series/EAH6770_DC2DI1GD5/](http://www.asus.com/Graphics_Cards/AMD_Series/EAH6770_DC2DI1GD5/) . To my knowledge, I am pretty sure the GPU can give off a better display.


So once Ubuntu found the drivers I needed, it installed them, and then restarted the computer. When the computer restarted, the screen did not fill the entire monitor. Instead the display gave off a smaller display with black bars around it. Then the text looked rather choppy. I tested out the video display by going and trying 1080p YouTube videos, but I noticed they were a little choppy as well...

At this point I don't know what's wrong...

Some help please??? :D

Uninstall the **fglrx** package and then reboot.

This time select the **other** AMD video driver offered in the Hardware screen.

---

