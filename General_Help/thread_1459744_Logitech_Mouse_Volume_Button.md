---
title: "Logitech Mouse Volume Button"
date: 2010-04-21
forum: General Help
---

### Post by physic.dude on 2010-04-21
I'm using the Logitech MX1100 mouse which has a quite a few buttons. (10) I would like to use 2 of them for volume control (as I do for Windows) but have no idea how to in ubuntu 9.10. Is there any way I could map the buttons to control volume?

I'm a minor noob so keep it simple...

---

### Post by kerry_s on 2010-04-21
i saw an applet in the repo you might want to try that.

---

### Post by physic.dude on 2010-04-22
Ok, I installed it, now what? How do I use it?

---

### Post by P4man on 2010-04-22
Maybe that applet works, I have no idea, should check it out. But if it doesnt work,  I currently use a different approach. Rather indirect, but it works. It does require (ab)using compiz.

First you need a little utility called xdotool

```
sudo apt-get install xdotool
```

Then in compiz config settings manager (if you dont have it, install it

```
 sudo apt-get install compizconfig-settings-manager
```

In compiz settings manager go to "commands" and create these two commands:

xdotool key XF86AudioLowerVolume
xdotool key XF86AudioRaiseVolume

Then in button binding, bind any mouse button to these commands.

Works like a charm ( I use the tilt wheel)

---

### Post by warfacegod on 2010-04-22
If you care to, you can change the percentage that the volume is increased or decreased by. The default is 6%. I found it very useful to adjust it lower for when I use my keyboard shortcuts.

Go to: Applications> System Tools> Configuration Editor> apps> gnome_settings_daemon> volume_step

Click the value and enter whatever # you prefer.

---

### Post by physic.dude on 2010-04-22
I have 10 buttons total on my mouse, not including the scrolling of the mouse wheel.

I found out what the buttons on the mouse  are mapped as in ubuntu

1- Left Click
2- Wheel down click
3- Right click
4- Scroll Wheel Foward
5- Scroll Wheel Back
6- Scroll Wheel Click left
7- Scroll Wheel Click right
8- Web page back
9- Web page forward

There are 3 more buttons that don't show up, 2 of witch I want to use for volume. I have circled the 3 buttons in the picture.

I know they say DPI but it was easily set as volume control in WinXP
Perhaps I need drivers?

Also, when I was in the Blender 3D modelling program it was using the button on the bottom as a rotating feature. So we know ubuntu can see the buttons.

---

### Post by P4man on 2010-04-22
open a terminal and type

> xev

a small white window will pop up. hover over it with your mouse, and press your buttons. It will give detailed info how ubuntu reads the clicks (if at all, but I strongly suspect it does).

You wont need a driver. You just need to assign a function to them. My approach should work for you if you have compiz. If there is an easier solution, then Ill gladly hear it.. but using compiz is great because I map other mouse buttons to compiz plugins like scale and expo and to rotate my cube (yeah i have way too many mouse buttons lol).

---

### Post by kerry_s on 2010-04-22
> **physic.dude said:**
> Ok, I installed it, now what? How do I use it?

it's an applet, right click your panel & add it.

---

### Post by physic.dude on 2010-04-22
Well, the thumb button is recognized but the 2 buttons that I want to use are not seen.

---

### Post by physic.dude on 2010-05-05
Bump

---

### Post by cheflo on 2010-08-17
Bump, I'm having the same issue. The thumb button is recognized in xev as Button10, but the two dpi/volume buttons are not seen. Has anyone found a workaround for assigning bindings to these two?

---

### Post by physic.dude on 2010-08-18
bump

---

### Post by kaderekusen on 2010-11-05
bumb i want it too

---

