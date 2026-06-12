---
title: "glxgears"
date: 2006-03-31
forum: General Help
---

### Post by groggyboy on 2006-03-31
so, a noob question, should be easily answered.

i'm curious to find out what my fps is with my computer.  i have a dell inspiron 6000 with intel i915 graphics card.  i can get glxgears to work from the terminal, but no fps output!  i poked around on the forums, and i've tried "glxgears --printfps", "glxgears -printfps", even "glxgears -iacknowledgethatthistoolisnotabenchmark" (someone on a forum had suggested that).  nothing!  the gears pop up, but no fps output of any kind that i can see!  what am i doing wrong? ](*,)

---

### Post by ComplexNumber on 2006-03-31
it should only necessary to put 'gxlgears' and thats it. afterabout 30 seconds or so, it should start pringing up the number of fps every 4-6 seconds or so in the terminal. what happnes when you do the same?

---

### Post by joelito on 2006-03-31
all you need to do

```

$glxgears -printfps

```

The fps will be printed every five seconds

---

### Post by krusbjorn on 2006-03-31
[QUOTE=joelito]all you need to do
The fps will be printed every five seconds[/QUOTE]

Well, read his post again ;)

---

### Post by groggyboy on 2006-03-31
cool.  boy do i feel silly. :mrgreen: 
> 5562 frames in 5.0 seconds = 1112.276 FPS
6747 frames in 5.0 seconds = 1349.323 FPS
6086 frames in 5.0 seconds = 1217.059 FPS
6181 frames in 5.0 seconds = 1235.799 FPS
6862 frames in 5.0 seconds = 1372.246 FPS
6071 frames in 5.0 seconds = 1214.153 FPS
6853 frames in 5.0 seconds = 1370.457 FPS
7023 frames in 5.0 seconds = 1404.565 FPS
7057 frames in 5.0 seconds = 1411.367 FPS
6918 frames in 5.0 seconds = 1383.543 FPS
8138 frames in 5.0 seconds = 1627.522 FPS
8165 frames in 5.0 seconds = 1632.959 FPS
7931 frames in 5.0 seconds = 1586.118 FPS
7987 frames in 5.0 seconds = 1597.243 FPS
7343 frames in 5.0 seconds = 1468.450 FPS
14737 frames in 5.0 seconds = 2947.371 FPS
10199 frames in 5.0 seconds = 2039.751 FPS


actually, that's alot better than i expected!  do you think i could run compiz + xgl?

curiosity has gotten ahold of me.

---

### Post by goslackware on 2006-03-31
current glxgears options:

-display
-info
-stereo
-fullscreen
-iacknowledgethatthistoolisnotabenchmark
-printfps

example:
glxgears -info -fullscreen -printfps

use, ctrl-c to exit glxgears while in fullscreen mode

and yes, it takes about 5 seconds for glxgears to display each count fps

---

### Post by ComplexNumber on 2006-03-31
[quote=groggyboy]cool.  boy do i feel silly. :mrgreen: 


actually, that's alot better than i expected!  do you think i could run compiz + xgl?

curiosity has gotten ahold of me.[/quote]
well, i don't see why not. give it a go - you've got nothing to lose. your fps is double what mine are and i've got a 1.8GHz pentium 4 with about 400MB of RAM...and thats after i've upgraded to the latest nVidia drivers too.

---

