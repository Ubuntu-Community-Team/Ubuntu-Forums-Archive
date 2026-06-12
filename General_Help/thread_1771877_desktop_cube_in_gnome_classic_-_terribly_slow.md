---
title: "desktop cube in gnome classic - terribly slow"
date: 2011-05-30
forum: General Help
---

### Post by u-noob-tu on 2011-05-30
today i decided i wanted to use the desktop cube again, so i went through all the compiz settings and got it working in gnome classic. however, when i initiate ratation with the mouse (ctrl>alt>button 1) it is sloooow whenever there is a window open (even just one). rotating away from the workspace with a window does seem to speed up the framerate. when i had maverick 10.10 it was never this slow. not sure why this is.

---

### Post by wildmanne39 on 2011-05-30
> **u-noob-tu said:**
> today i decided i wanted to use the desktop cube again, so i went through all the compiz settings and got it working in gnome classic. however, when i initiate ratation with the mouse (ctrl>alt>button 1) it is sloooow whenever there is a window open (even just one). rotating away from the workspace with a window does seem to speed up the framerate. when i had maverick 10.10 it was never this slow. not sure why this is.
Hi, I have mine set up in unity it is working perfectly, but it took a lot of tweaking and installing with instructions just for natty. You change your refresh rate to 60, and in opengl in ccsm make sure sync to vblank is not checked, and if you are using nvidia card go into nvidia x server manager and make sure sync to vblank is not checked there also and set refresh rate to 60 in there also.

---

### Post by wildmanne39 on 2011-05-30
> **u-noob-tu said:**
> today i decided i wanted to use the desktop cube again, so i went through all the compiz settings and got it working in gnome classic. however, when i initiate ratation with the mouse (ctrl>alt>button 1) it is sloooow whenever there is a window open (even just one). rotating away from the workspace with a window does seem to speed up the framerate. when i had maverick 10.10 it was never this slow. not sure why this is.
Hi, I ran across this for the cube in ubuntu classic that should take care of your problems if changing those setting do not.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by u-noob-tu on 2011-05-31
tried downgrading compiz. it helped a little but it still stutters a lot. not sure why. in maverick it was smooth as butter.

---

### Post by BrokenKingpin on 2011-05-31
What graphics card are you running... do you have the proprietary drivers enabled?

---

### Post by u-noob-tu on 2011-05-31
> **BrokenKingpin said:**
> What graphics card are you running... do you have the proprietary drivers enabled?

i have an intel integrated chip. as far as i know its the mesa driver, whichever one comes by default as i havent needed to mess with the drivers. i had the same driver for maverick (though i probably have a newer version now).

---

### Post by wildmanne39 on 2011-05-31
> **u-noob-tu said:**
> i have an intel integrated chip. as far as i know its the mesa driver, whichever one comes by default as i havent needed to mess with the drivers. i had the same driver for maverick (though i probably have a newer version now).
Hi, did you change those setting I mention in my other post after you downgraded?

---

### Post by u-noob-tu on 2011-05-31
> **wildmanne39 said:**
> Hi, did you change those setting I mention in my other post after you downgraded?

yeah, they are all set the way you suggested. still choppy framerate.

---

### Post by wildmanne39 on 2011-05-31
> **u-noob-tu said:**
> yeah, they are all set the way you suggested. still choppy framerate.

Hi, I am out of suggestions, I do have it working perfectly in unity,it surprised that it works so good after I changed several settings.

---

