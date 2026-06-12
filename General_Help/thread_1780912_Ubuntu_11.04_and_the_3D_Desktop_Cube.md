---
title: "Ubuntu 11.04 and the 3D Desktop Cube???"
date: 2011-06-12
forum: General Help
---

### Post by tinker88 on 2011-06-12
I have Ubuntu 11.04 and I am running it on Ubuntu classic due to not caring for Unity very much. I have an Acer Aspire 5739 and a Nvidia GEForce GT 130M graphics card. Is there any way to have a 3D desktop cube again? 

I have read many posts on here and else where and still have not managed to get it working. Someone please help me (I am fairly new to Linux btw so just try to keep that in mind when replying) Thanks!!!

---

### Post by sikander3786 on 2011-06-12
Did you try this one?

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

It is fairly easy stated I guess so you don't need much of a geeky knowledge for that :)

---

### Post by tinker88 on 2011-06-13
i tried it now ...still no cube....maybe im just not meant to have the cube anymore

---

### Post by pqwoerituytrueiwoq on 2011-06-13
you may need the compiz plugin extras also be sure you have ccsm installed (maybe in the universe repository)

---

### Post by pritam_par on 2011-07-25
[FONT=Arial][SIZE=2]Enabling Cube with unity will kill the unity. This can be solved just follow the process below

1.In compiz setting manager disable these plugin:
[/SIZE][/FONT] [FONT=Arial][SIZE=2]            i) OpenGL[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]            ii) Composite[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]            iii) Ubuntu unity plugin[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]           iv) Desktop wall.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]    Select ***disable plugins*** when a window appears asking for disabling other plugins.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]After disabling these plugins your panels and unity will disappear,don't panic and follow next step.

2. Now enable these plugins sequentially. [/SIZE][/FONT]  
[FONT=Arial][SIZE=2] [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]        i)OpenGl[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT] [FONT=Arial][SIZE=2]       ii)Composite[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT] [FONT=Arial][SIZE=2]      iii)Desktop cube [/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT] [FONT=Arial][SIZE=2]      iv)Rotate cube[/SIZE][/FONT]
[FONT=Arial][SIZE=2]        v)Ubuntu unity plugin.

And you are done.
[/SIZE][/FONT]

---

### Post by altjx on 2011-10-29
> **pritam_par said:**
> [FONT=Arial][SIZE=2]Enabling Cube with unity will kill the unity. This can be solved just follow the process below

1.In compiz setting manager disable these plugin:
[/SIZE][/FONT] [FONT=Arial][SIZE=2]            i) OpenGL[/SIZE][/FONT]
[FONT=Arial][SIZE=2]            ii) Composite[/SIZE][/FONT]
[FONT=Arial][SIZE=2]            iii) Ubuntu unity plugin[/SIZE][/FONT]
[FONT=Arial][SIZE=2]           iv) Desktop wall.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    Select ***disable plugins*** when a window appears asking for disabling other plugins.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]After disabling these plugins your panels and unity will disappear,don't panic and follow next step.

2. Now enable these plugins sequentially. [/SIZE][/FONT]  
[FONT=Arial][SIZE=2]        i)OpenGl[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       ii)Composite[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]      iii)Desktop cube [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]      iv)Rotate cube[/SIZE][/FONT]
[FONT=Arial][SIZE=2]        v)Ubuntu unity plugin.

And you are done.
[/SIZE][/FONT]

Bringing back an old thread if you guys don't mind... My compiz settings manager closes out as soon as I disable openGL. any idea what else I could try to accomplish this as well?

---

