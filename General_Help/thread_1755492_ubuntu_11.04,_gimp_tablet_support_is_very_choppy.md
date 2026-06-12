---
title: "ubuntu 11.04, gimp tablet support is very choppy"
date: 2011-05-11
forum: General Help
---

### Post by handlebar on 2011-05-11
Hi People

I have a wacom intuos3 and with unity turned on the brush behaviour in the gimp becomes very choppy.
Things are fine if i switch to the old gnome panels with no effects so it must be a unity thing.
Any suggestions on a fix for this would be great, thanks.
I'm using 64bit natty, and gimp from the repositories.

---

### Post by phatcartoon on 2011-05-11
I don't really seem to have this problem. I am using Ubuntu 11.04 (natty) 64bit and an Intuos 3, and for the most part GIMP works fine. The only problem I have with GIMP is sometimes it won't recognize the pen pressure/stroke. If this happens I just lift the pen again and it starts working. A little annoying, but GIMP has always been buggy for me.

What do you mean by choppy? Do you mean delayed or slow to respond? Do you encounter this in any other programs? Try using MyPaint and see if you have the same problem. When I use MyPaint my tablet works flawlessly. I love MyPaint. :D

The problem I am having is the pressure sensitivity isn't working at all in programs like, Pencil, or Krita Paint. I really like using Pencil and for it not to work with my tablet is quite frustrating.

---

### Post by handlebar on 2011-05-11
I mean when trying to use the brush engine, sometimes a stroke will stick and the cursor wont move, makes it almost impossible to paint with. 
My Paint and blender seem to work fine, seems to be a unity gimp issue
Everyone i've asked on the blender forums has the same problem, and the only workaround seems to be to use the old gmome panels without effects.

---

### Post by angelcleff on 2011-05-18
Hey!  same problem here :(
i have a intuos 4 and when i start drawing  some lines get painted some others not ... why is that??.... is so annoying :( also im using the open source drivers for my ati card cuz with the proprietary ones unity gets very laggy

---

### Post by rudeboy1 on 2011-06-04
Yeah having the same problem Inkscape works well but can't get pressure to work and in gimp pen only works about half of the strokes and no pressure haven't tried any others yet.

---

### Post by rabe42 on 2011-06-24
I can confirm this behaviour also for the Genius MousePen i608. The problem seems to be connected to compiz or whatever is responsible for effects. It seems not to be related to unity, since you can get the same problems, using Gnome 2 support with effects.  The effects seems to consume every second touch down of the pen.  Switching to Gnome 2, without effects seems to be the only way to address this problem at the moment.

---

### Post by slug45 on 2011-07-21
> **rabe42 said:**
> i can confirm this behaviour also for the genius mousepen i608. The problem seems to be connected to compiz or whatever is responsible for effects. It seems not to be related to unity, since you can get the same problems, using gnome 2 support with effects.  The effects seems to consume every second touch down of the pen.  Switching to gnome 2, without effects seems to be the only way to address this problem at the moment.

+1

---

### Post by Vyoma on 2011-08-03
I can confirm this.

Details:
[LIST]
[*]Ubuntu 11.04
[*]GIMP
[*]Intuos3
[*]Dell Studio XPS
[/LIST]

When using Unity or Gnome with effects, the response to brush strokes is very choppy.

Switching to Ubuntu Classic without effects, brush strokes are very responsive similar to what I wax getting with Ubuntu 10.10 - I have not tried it with MyPaint or other software.

Do we need to raise a defect some where? Which project would be more appropriate?

---

### Post by lachoneus on 2011-09-03
I can confirm this as well.

I am running Dreamstudio 11.04, with a USB Intuos 4 tablet, and the tablet only works smoothly when I run Dreamstudio desktop without effects.  Choppy when I use Unity, or classic interface with effects.

It seems like I have had issues with Compiz and my tablet before.  Could this be the problem?

---

### Post by ragtag on 2011-09-03
The brush stroke not showing up seems to relate to a conflict between the toolbox windows being on top and compiz. A work around is to go into Edit>Preferences>Windows Management, and set both the Hint for the toolbox and Hint for other docks to "Normal window". After that Unity and the GIMP seem to play nice together. It has the downside, that the toolbox is no longer always on top of the canvas, and setting the Toolbox to be alwyas on top by using the right click menu in it's title bar, re-introduces the original problem. Alternately you can log in to Classic/No-effects mode.
:)

rudeboy1: To get pressure in GIMP, go to Edit>Preferences>Input Devices and click the "Configure Extended Input Devices..." From the Device menu, select you stylus, eraser etc, and set the Mode to Screen. After that you should have pressure in GIMP.

---

