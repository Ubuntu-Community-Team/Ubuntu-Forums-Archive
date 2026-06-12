---
title: "Problem with using separate x-screens with laptop and tv"
date: 2010-02-05
forum: General Help
---

### Post by Simpsoni28 on 2010-02-05
Hi guys,

I've been plagued with problems with my laptop and linux (mainly graphics problems) but I've worked through them with your help and a bit of ingenuity!

I have a Sony Vaio CW with a nvidia 230m graphics card running ubuntu 9.10 64bit and a 32" Samsung HD LCD TV which I connect via VGA (will be HDMI at somepoint when I buy another cable). However, in linux when I connect the vga cable and boot the laptop both screens activate and I get a separate x-screen on both, brilliant!

However, I have 2 problems:

1) I want the laptop screen to be the main screen not the tv but I cannot find an option to switch them as all my shortcuts are on the tv but I dont want it like that!

2) When I disconnect the VGA cable, the laptop does not realise that it isn't connected to a TV anymore and the obviously this means that I cannot login (as the login box is on the tv screen!) and also my shortcuts aren't there! The mouse can still go upwards and enter the non-existant TV screen!

Any ideas?

---

### Post by Simpsoni28 on 2010-02-08
Well, i've managed to get the laptop screen as the main screen by jiggling around the way it was selected... (basically, it just started working!)

However, the other issue remains where unplugging the VGA cable doesn't stop ubuntu thinking that there are no external monitors plugged in...

Also, another issue has arisen. Every 5 mins or so the screen goes black if I don't do anything which is really, really annoying if i'm trying to watch a movie or something...

Hope someone can help...

---

### Post by chewearn on 2010-02-08
Regarding the problem assigning default screen to laptop screen and secondary screen to TV, see my blog post here: [http://blog.chewearn.com/2008/10/09/nvidia-separate-x-screen-in-intrepid-ibex-beta/](http://blog.chewearn.com/2008/10/09/nvidia-separate-x-screen-in-intrepid-ibex-beta/)

Scroll down to step 12.

---

### Post by efflandt on 2010-02-08
Under System > Preferences check your Screensaver and Power Management settings.  There are check boxes about monitor dimming, and separate Power Management settings for AC or battery.

---

### Post by Simpsoni28 on 2010-02-08
Ok, that seems to have fixed a few problems, my laptop is now the main screen and the screen doesn't go dark anymore.

I have one problems remaining:

When the VGA cable is removed, the laptop doesn't realise there is only one screen and as a result the mouse can leave the top of the screen as though the tv was stilled connected! Which is annoying (but I can live with it...)

---

