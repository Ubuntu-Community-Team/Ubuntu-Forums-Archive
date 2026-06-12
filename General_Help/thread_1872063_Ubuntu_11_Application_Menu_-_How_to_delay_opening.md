---
title: "Ubuntu 11 Application Menu - How to delay opening"
date: 2011-10-30
forum: General Help
---

### Post by requeth on 2011-10-30
Hello,

I just upgraded from Ubuntu 10 to 11.10 and I'm getting very frustrated. The application bar set on the left side of the screen is infuriating. When I'm trying to hit the back button on my browser or hit buttons in applications the damn bar pops out and takes over focus.

Does anyone know of a way to have it only come out if I'm pressing Ctrl or something while hovering over? Or setting a longer delay so I have to hover over it for 3 seconds?

Right now it takes me 4-5 seconds to press the back button each time because I have to slowly inch up to it. First it was taking away Gaim and adding the POS Empathy, and now it's taking away a perfectly good taskbar and putting in the most annoying feature of mac.

---

### Post by dFlyer on 2011-10-30
I've been using 11.10 since beta1 and I'm not sure what your talking about. I've no problem. Can you provide any extra information. I find unity very stable.

---

### Post by lynrock on 2011-10-30
Just install Compizconfig Settings Manager and look for the Unity plugin. There are various settings for the launcher there.

---

### Post by guestolo on 2011-10-30
> **lynrock said:**
> Just install Compizconfig Settings Manager and look for the Unity plugin. There are various settings for the launcher there.

That should do it
In Compizconfig settings manager
Under General>>General Options
Try setting "Edge Trigger Delay" from 0 to something like 2800 or a bit less

---

### Post by lolpenguin on 2011-10-30
Run these first:
```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```
Now launch CCSM, click on "Ubuntu Unity Plugin" under "Desktop".
Change the value of "Edge Reveal Timeout" to the number of milliseconds you want to delay the reveal of the Unity launcher.
There should now be a delay when you move the mouse to the edge of the screen
Cheers :D

OR alternatively you can disable reveal mode when moving the mouse to the left edge. Change the value for "Reveal Mode" to none. The launcher will now only show when you hold down the [Super] key

---

### Post by requeth on 2011-10-30
I got all excited and installed compiz, but the max delay is 1,000 and any configuration on that bar has no visible effect.

Putting in None for "Edit Reveal Mode" I receive an error stating that "" is not a valid edge mask. (I'm typing in the word None). I tried just leaving the field blank and received the same message.

Looks like this is what I want, but someone has coded these options out for some reason.

Any other ideas?

---

