---
title: "Blender Interface unresponsive, no buttons work"
date: 2010-01-02
forum: General Help
---

### Post by Saronn on 2010-01-02
The interface in Blender doesn't work. The buttons don't do anything when I click on them, but I can still hold middle button and look around in the 3D view. What's going on?

Using Ubuntu 9.04, Blender 2.49b (Python 2.6)

---

### Post by Saronn on 2010-01-02
bumpy bumpy

---

### Post by Saronn on 2010-01-03
Anyone have any suggestions or anything?

---

### Post by warfacegod on 2010-01-03
I have no idea what Blender is but try looking for something that says unlock. That should ask you for your password to unlock the app.

---

### Post by MindFusion on 2010-01-03
Maybe you should try turning off Compiz if enabled? Some apps don't work with me if compiz is still enabled.

---

### Post by Saronn on 2010-01-03
I didn't have compiz enabled, so I tried enabling, doesn't work :c

EDIT: Also, the terminal output doesn't say anything, so don't ask for that

---

### Post by Vinomfire on 2010-01-04
i'm having the same exact problem. i reinstalled it from their website but it still doesn't work. i'll try turning off compiz and see if that works.

---

### Post by mickie.kext on 2010-01-04
@Saronn & Vinomfire

Which graphics cards do you guys have, and which drivers are you using?

Do keyboard commands work? For example, S key should allow to resize that cube in the middle, and spacebar should bring up context menu. Also, try to start Blender in windowed mode, if you started it in full screen

---

### Post by Vinomfire on 2010-01-04
all of my keyboard function work in blender. the graphics driver that i am using is called "ATI/AMD proprietary FGLRX graphics driver". i wouldn't be surprised if this is a driver issue. earlier i tried running a netbeans-3d game program and it failed. i tried turning off alot of my compiz settings, but that didn't work either.i think i'll try downloading an older version of blender to seee if that works.

---

### Post by Saronn on 2010-01-04
Yea, keyboard functions work, and my graphics controller(?) is Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller, hopefully that's what you meant :U

EDIT: apparently are invisible, i pressed space and stuff would happen when i clicked around. Same thing with all the windows..

OKAY, THIS IS NOW NOT AN INTERFACE PROBLEM, THE MENUS ARE JUST INVISIBLE, and i don't really think anything else...

---

### Post by Saronn on 2010-01-05
Please, could someone help?? I really want it to work.

---

### Post by Saronn on 2010-01-05
HEY GUISE, I GOT IT WORKING!

What you do is you make a shell script(?lol) and in it, write LIBGL_ALWAYS_SOFTWARE=1 blender.

Save it as blender.sh, make it executable, and there you go!

(hopefully you have it installed through the repositories, I think thats how it works... :l)

---

### Post by Vinomfire on 2010-01-10
glad you got it working, but i still have the same problem. when i run the shell script, blender opens, but the menus are invisible. if i hit the space bar, nothing pops up, but if i click the screen where there should be the create cube option,it makes a cube. the same problem you were having.could you post exactly what you put in the shell script and what you mean by repositories. thanks

---

