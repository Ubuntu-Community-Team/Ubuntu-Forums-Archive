---
title: "Rotating the screen"
date: 2009-10-13
forum: General Help
---

### Post by Poderoso on 2009-10-13
Hi,

how do you rotate the screen 180 degrees? I have managed to rotate it 90 degrees by adding the line ' Option "Rotate" "CW" ' (or CCW) in xorg.conf but I haven't figured out how to do a 180?

---

### Post by Lori700698 on 2009-10-13
If your looking for the cube thing have a look at these directions.

[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by uberg on 2009-10-13
If you are using Gnome - System/Preferences/Display will let you rotate the orientation.  Is that what you are looking for?

---

### Post by Poderoso on 2009-10-14
> **uberg said:**
> If you are using Gnome - System/Preferences/Display will let you rotate the orientation.  Is that what you are looking for?

I am using Gnome but I have an Nvidia graphics card and I'm using the Nvidia drivers (180) so there is no option for rotating the screen under "Display". Like I said, I can get rotation done by editing the xorg.conf but only up to 90 degrees so I was wondering if there even is a simple way of doing the 180 degree rotation by adding something else to xorg.conf than "CW".

And no, the "cube thing" is most likely not what I'm looking for. I just want everything to be upside down on the screen because of a very custom monitor setup I have.

---

### Post by Poderoso on 2009-10-14
Nm, I figured it out. One way to do it at least.

I added this line: Option          "RandRRotation" "on"
Under: Section "Device"

Now I get the option of rotating the screen in the nvidia X server Settings.

---

### Post by uberg on 2009-10-14
Good.  I get the shakes anytime I consider editing the X file.  So REALLY Good.  And congratulations.

---

