---
title: "laptop resolution problems"
date: 2010-07-09
forum: General Help
---

### Post by haxxxorz21 on 2010-07-09
in my laptop installation of ubuntu karmic, because the resolution out-of-the-box was way bigger than my laptop's actual display, i had to use the "virtual" option in my xorg.conf file. 

everything is fixed, but now everytime i fullscreen in chocolate-doom,zsnes, or any other program that switches to low-res mode to do fullscreen, it makes a funky pattern across the screen that locks me out of my computer. any suggestions?

peease reply

---

### Post by TBABill on 2010-07-09
Do you have a proprietary driver available for use on your video card? Which graphics card do you have? Typing lspci in a terminal will let you know if you are unsure, but you will have to scroll through the results to find the graphics card part since it will report lots of hardware.
 
Normally the proprietary driver will fix issues if one is available. You may be using a generic vesa driver at the moment, causing issues when your resolution changes. The proprietary drivers are much better at controlling your GPU and keeping the desktop as neat as it can be visually.

---

### Post by haxxxorz21 on 2010-07-13
my laptop doesnt have a graphics card.

---

### Post by mr clark25 on 2010-07-13
it should have a graphics card built in...

could post the output of
```

lspci

```


this will help us help you ;)

---

### Post by Twitch6000 on 2010-07-13
What laptop do you have. Most have graphics cards. If it does not have a graphics card your resolution would not be above 640x468 .

---

