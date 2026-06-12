---
title: "Volume applet missing?"
date: 2010-01-18
forum: General Help
---

### Post by Kareeser on 2010-01-18
So for some reason... I can't seem to re-add my volume applet to my panel after I deleted it, on my **karmic** install

It used to be listed under "Volume"-something, in the "Add to Panel" window, but it's disappeared.... hm.

Anyone know how I can get it back?

---

### Post by michy99 on 2010-01-18
The volume control is usually part of the notification area. Perhaps you removed the notification area. See if adding it fixes things.

---

### Post by MoRoBoShi on 2010-01-18
uh.. that's true rigth clicking > add to panel doesn't show any "volume applet" 
but if I unlock notification area I move my volume icona along with all other systray's icons..
Have you try to add  Notification area? (maybe try toremove and readd..)

---

### Post by Kareeser on 2010-01-18
hm... well look at that. It looks like the volume app was integrated into the notification area.

Cheers for that!

---

### Post by Gozer42 on 2010-01-20
The removal of the standalone volume applet was a bad move.  I don't want anything else the notification area applet on my panel, but I do want a volume control.

Furthermore, I always placed my volume control applet in the corner of the screen.  This made it instantly accessible by warping my mouse to the corner and using the scroll-wheel to change the volume.  I didn't have to watch the mouse cursor, I could just quickly drag it to the corner and change the volume.

Now I have to watch the cursor and make sure it is on the speaker icon in the notification area before changing the volume.

This is a UI issue that has regressed in Ubuntu 9.10.

I beg developers to bring back the simple volume control applet.

---

### Post by m4tic on 2010-01-21
Sometimes the volume applet may crash due to updates, transferring your home folder to a new install or a bad boot, if re-adding the notification area does not work, try deleting ~/.pulse , don't worry it will recreate itself

---

### Post by Yellow Pasque on 2010-01-21
If you want the old volume control back, get gnome-media and gnome-applets packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
I don't know how well that will work if you're running pulseaudio though.

---

