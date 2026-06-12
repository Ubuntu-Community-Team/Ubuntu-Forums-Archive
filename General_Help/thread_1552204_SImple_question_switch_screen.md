---
title: "SImple question switch screen"
date: 2010-08-13
forum: General Help
---

### Post by shivan000 on 2010-08-13
Heya

I have 10.04 lts running with compiz + cube running. I have a 22' lcd (via vga) and a 40' lcd (via hdmi) connected up. I don't wont to run twin-view or separate x screens. 

All i want to do is change the screens. It boots up to the 22', how do i swap the output to the 40'. 

Currently i shutdown my PC, unplug the VGA and it boots up with the 40' screen.

???

---

### Post by sydbat on 2010-08-13
> **shivan000 said:**
> Heya

I have 10.04 lts running with compiz + cube running. I have a 22' lcd (via vga) and a 40' lcd (via hdmi) connected up. I don't wont to run twin-view or separate x screens. 

All i want to do is change the screens. It boots up to the 22', how do i swap the output to the 40'. 

Currently i shutdown my PC, unplug the VGA and it boots up with the 40' screen.

???First - what is your video card? If it is nVidia, the nVidia X Server Settings interface (found under System > Administration) allows you to choose which monitor is 1 and which is 2. Then, when booting, it will choose display 1 as the primary (in your case, the 40").

I imagine that there are the same types of controls for an ATI card. However, I would defer to someone with that knowledge to help you out.

---

### Post by aeiah on 2010-08-13
i do this with an nvidia card, a 19" monitor and an HDTV. i press a button on my remote control and a script switches things over for me and starts up xbmc. basically it exports a new x session to the specific screen i want. its a bit complicated, but you can set it to be automatic. 

like has been said, you can do it manually with nvidia-settings.. you can also do it with most graphics card utilities and such like xrandr and its gui counterparts if you're using intel drivers or something.

my method is described here:

[http://ubuntuforums.org/showpost.php?p=8835078&postcount=2](http://ubuntuforums.org/showpost.php?p=8835078&postcount=2)

but that might seem rather complicated.

---

