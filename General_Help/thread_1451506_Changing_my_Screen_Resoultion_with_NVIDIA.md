---
title: "Changing my Screen Resoultion with NVIDIA"
date: 2010-04-10
forum: General Help
---

### Post by VEI2I7AS on 2010-04-10
OK so i had to run recovery mode and all my original settings were lost.. boohoo ill get over it. soon enough itll be back to normal. BUT the main reason i had gotten so screwed up before is because i was trying to change my screen resolution. Now from having my computer for a month or so ive realized there are many diff verisons of Ubuntu and many ways of doing things. All im trying to do is change my screen from 640x480 to a more viewable size, cant think of the dimensions right now. Im running NVIDIA graphics and when i try to run display preferences from settings it obviously won't open cause it isnt configured. Can anyone help?

thankyou

---

### Post by moetunes on 2010-04-10
Have you installed the resticted drivers from the menu?
You can make a xorg.conf with the command
> Xorg -configure
then edit the file to your liking and then move it to /etc/X11.

---

