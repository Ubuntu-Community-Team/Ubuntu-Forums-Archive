---
title: "Wii Remote button mapping"
date: 2010-09-29
forum: General Help
---

### Post by trustnoone on 2010-09-29
Hi
I just started testing using a Wii remote for moving my mouse on Ubuntu :D so far its been heaps awesome, I'm a little confused how the IR part works but the accelerometers seem to be working a charm

The problem I'm having is button mapping (yeah I'm a noob :) ) the problem is I have (fn+f10) for volume up and (fn+f9) for volume down, on my keyboard. But I don't get how to do this on the Wii remote

I'm able to get to the part where you change the buttons like
Wiimote.Minus	= KEY_F9
Wiimote.Plus	= KEY_F10

But I don't get how to make the "Wiimote.Minus" part to press the fn key and also F9
or even if I have the fn key as a different button I'm not sure exactly what I'm supposed to add like (KEY_FN)????

Thanks Heaps
----------------------------------------------------------------
Okay not sure if people need it but I found
Wiimote.Minus	= KEY_VOLUMEDOWN
Wiimote.Plus	= KEY_VOLUMEUP
for the volume control, still working on Play and Pause though and also next/back
-------------------------------------------
Okay I found everything I needed thanks anyways, took lots of googling, and the main thing i needed I kept missing an didnt try googling >.> typical typical
anyways if anyone needs a list of the different input for the Wii mote its
[http://abstrakraft.org/cwiid/browser/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/wminput/action_enum.txt) at that site
the previous one i kept trying seems to not work >.>

---

