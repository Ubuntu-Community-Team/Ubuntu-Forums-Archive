---
title: "Need drag-lock, PLEASE!"
date: 2011-08-24
forum: General Help
---

### Post by CaptSaltyJack on 2011-08-24
On most other PCs and Macs with a touchpad, you can double tap to start dragging, and if you need to move something a great distance, you can let up on the touchpad just for a second and reposition your finger on it, and you will still be in drag mode, until you let off your finger for a certain amount of time, or you single tap. Is there some way to do this in Ubuntu 11.04?

---

### Post by CaptSaltyJack on 2011-08-24
Bam, just solved my own prob!

Install xinput if it's not already, then type "xinput list" to see your devices. Look for the trackpad and make a note of its id# (mine is id=12).

Then do "xinput list-props 12 | grep Lock" (replace '12' with whatever your ID is) and you'll see options for locked drags and a timeout value. Make a note of their ID#s (in parentheses) for easy access. You want to set locked drags to 1, and timeout to whatever is comfortable for you (350ms is good for me).

Type: xinput set-prop 12 259 1 (259 is my ID for Locked Drags)
And: xinput set-prop 12 260 350 (260 is my ID for Locked Drags Timeout)

Works like a charm!

---

### Post by roxyland on 2011-09-19
Awesome !!! Been looking to get this working on my mac magic trackpad for a while now and had almost given up. Was getting real frustrating not having the locking drag. Thanks !

---

### Post by ninjaherring on 2011-09-23
Thanks.

---

### Post by duboisj on 2012-01-02
On my box, just in case anyone else is trying to get this going, I also set: 

Synaptics Tap FastTap  to 1 (this was pretty much necessary to get tap-to-drag of window-bars to work)
Synaptics Palm Detection  to 1 (this may have helped with false-fires of the touchpad from my palm while typing)

I am running on  MacBookPro8,2 (thats a late-2011 15-inch model) with Ubuntu 11.10 (A custom kernel is necessary to run on this hardware: I don't know how much of my setu.p differs from the norm b/c of that, but that's my mileage).

The FastTap thing really improved my experience b/c I like to tap-drag windows.  Right now I don't have it working as well for text selection, for some reason, but it's still better.

Cheers.

---

### Post by CaptSaltyJack on 2012-06-05
Another tip:

To apply the settings to all users, instead of pasting the lines above into ~/.xinput.d/en_US, paste them into /etc/X11/xinit/xinput.d/en_US.

---

### Post by podcast on 2012-07-23
Thank you for this nice tips.

I wonder is there an option to activate locked drags after a little time if the tap is continue.

Windows allow to set this little time. To activate click lock the mouse button should holded down during this little time.

In Ubuntu, drag starting with no delay. I searched and tried somethings but no result.

Any idea?

---

### Post by lisati on 2012-07-23
> **podcast said:**
> Thank you for this nice tips.

I wonder is there an option to activate locked drags after a little time if the tap is continue.

Windows allow to set this little time. To activate click lock the mouse button should holded down during this little time.

In Ubuntu, drag starting with no delay. I searched and tried somethings but no result.

Any idea?

Your previous request has been moved here: [http://ubuntuforums.org/showthread.php?t=2032043](http://ubuntuforums.org/showthread.php?t=2032043)

Old thread closed.

---

