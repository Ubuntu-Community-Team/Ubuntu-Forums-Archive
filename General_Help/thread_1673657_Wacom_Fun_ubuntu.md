---
title: "Wacom Fun/ ubuntu"
date: 2011-01-22
forum: General Help
---

### Post by Cloudkookoo on 2011-01-22
So this issue may be a little bit difficult to describe so bear with me. I'm using a wacom fun pad with a mouse and pen device. My problem is that when i touch the pad with the pen, the cursor on screen moves to the position relative to where the pen is on the pad. If I touch the top right of the pad, the cursor instantly goes to the top right corner of the screen, likewise for the other corners.

The mouse is different however, no matter where the cursor is on screen, if i place mouse on the pad, the cursor remains stationary and moves only when the mouse is moved, rather than moving to the place the mouse was placed.

I want the pen to behave the way the mouse does, because that's how it's working on Windows and that's what I'm used to. The way it is now is very difficult to draw with... which is my entire purpose for using the pen device. Is this a driver issue? Or some setting that I need to adjust?

---

### Post by Favux on 2011-01-22
Hi Cloudkookoo,

Right now the stylus is in the Absolute Mode and the Wacom tablet mouse in Relative Mode.  Those are the linuxwacom defaults.  You can modify behavior by using the xsetwacom Mode command.  However be warned that using the Mode command will stop you from pulling guidelines in Gimp with your mouse due to a current gtk (gnome tool kit, for windowing graphics) bug.

First you get the device name of your stylus by entering in a terminal:
```
xinput list
```
Then with quotes the command is:
```
xsetwacom set "Wacom BambooFun 4x5 stylus" Mode "Absolute"  # or Relative
```
Where in this example the stylus device name is "Wacom BambooFun 4x5 stylus".  And of course you would swap Relative for Absolute.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") post #2 for a sample xsetwacom script for the Bamboo.

---

### Post by Cloudkookoo on 2011-01-22
Yes! Thank you for the quick response, it worked like a charm.

---

### Post by Favux on 2011-01-22
Great!

Please mark the thread as solved using the post tools above your first post.

---

