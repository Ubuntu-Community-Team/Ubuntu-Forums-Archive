---
title: "Compiz Config Settings Manager (CCSM) Problem"
date: 2011-12-05
forum: General Help
---

### Post by seojunkim on 2011-12-05
System:
Samsung Sens R60 Plus
Celeron 530 M 
ATI Radeon X1250
Motherboard: Phoenix 
Display: 1200x800
Operating System: Ubuntu 11.10
____________________________
I am trying to turn off the PNG function in CCSM in order to avoid graphic problem in unity 3D, however, whenever I untick the PNG function, CCSM just shuts down without doing anything. Help! 
(I have Unity 2D, so please don't say "get unity 2D" because I am trying to get unity 3D work on my desktop once again. Thank You :o)

---

### Post by BC59 on 2011-12-05
> **seojunkim said:**
> System:
Samsung Sens R60 Plus
Celeron 530 M 
ATI Radeon X1250
Motherboard: Phoenix 
Display: 1200x800
Operating System: Ubuntu 11.10
____________________________
I am trying to turn off the PNG function in CCSM in order to avoid graphic problem in unity 3D, however, whenever I untick the PNG function, CCSM just shuts down without doing anything. Help! 
(I have Unity 2D, so please don't say "get unity 2D" because I am trying to get unity 3D work on my desktop once again. Thank You :o)

The drastic solution is to reset your Compiz.

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

---

### Post by seojunkim on 2011-12-05
> **BC59 said:**
> The drastic solution is to reset your Compiz.

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

Thank you so much. It worked perfectly. :)

---

### Post by BC59 on 2011-12-05
Always welcome. Please mark the thread as Solved from the thread tools.

---

