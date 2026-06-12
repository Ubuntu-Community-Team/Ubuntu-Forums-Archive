---
title: "Blender: Invisible menus"
date: 2009-11-15
forum: General Help
---

### Post by Tickborn on 2009-11-15
Hi everybody.
I installed Blender on Ubunto Karmic. It starts fine, but when i try toopen a menu, it simply doesnot show up: it is just invisible, infacts i can stillblindly  click on it an something will eventually  happen.
In the past i had a similar problem in Kubuntu, but i needed simply to press <Alt+Cntr+F2> to temporarily de-activate Composite.
Now the questions are:
1. How do i  do that in Ubuntu?
2. Is it a known issue?
3. Is it due to my configuration? (ATI 4850 video card with AMD driver installed. Compiz+Emerald for windows and desktop decoration)

Thanx in advance

---

### Post by Tickborn on 2009-11-17
Is there really anybody using Blender out there? :)
Help!

---

### Post by natnhos on 2009-11-20
I'm having a different problem.  Blender just fails to open.  I was having similar problems to yours in Jaunty, though.  I just got used to the hot keys and worked around it.  I'm running a similar graphics card on a P4.  I hope someone can help us, cause I have a lot of work to do...  ](*,)

For now, I'm gonna try turning off some effects.  That seems to be the source of many problems in Ubuntu.

---

### Post by natnhos on 2009-11-20
nope...  still nothing.

---

### Post by henriq on 2009-11-22
This problem has to do with compiz. I solved it on my computer by going into CompizConfig settings manager -> Workarounds -> Legacy Fullscreen Support checked. This will fix the menu problem. However, Blender became unstable and trying to alt+tab out of it or switch desktop made the whole desktop freeze. Try if it works for you.

To run blender in a stable way I had to disable compiz. Do this by typing metacity --replace& in a terminal before launching blender. Type compiz --replace& when you are done to restart compiz.

I run blender from a simple shellscript that does this automatically:
type

metacity --replace&
blender
compiz --replace&

in a file called blender.sh. Make it executable and run it by typing ./blender.sh.

Only launch one instance of blender at a time with this script though, if you want to have multiple blender instances do it the manual way, otherwise things will get messy when you close one of the windows.

/Henriq

---

### Post by Tickborn on 2009-11-23
:p Thanx everybody for answering! So apparently the problem is not new and it is a compatibility problem.
The solution proposed by Henriq is a great help to fast up  when you want to start Blender.
I will anyway leave this thread open, to see if anybody can add more solution, or at least in the hope to sensibilize to the problem ;)

---

### Post by emigrant on 2009-11-23
By the way i like ur avatar very much :D

---

### Post by Tickborn on 2009-11-24
> **emigrant said:**
> By the way i like ur avatar very much :D

:cool: Thanx

---

### Post by cyqotiq on 2009-12-23
> **henriq said:**
> I run blender from a simple shellscript that does this automatically:
type

metacity --replace&
blender
compiz --replace&

in a file called blender.sh. Make it executable and run it by typing ./blender.sh.


I had the "invisible menus" problem on Ubuntu Karmic 64 with an ATi card and the proprietary driver installed.  Henriq's suggestion seemed to work great!

---

### Post by bli_wedhooz on 2010-05-04
newbie need help.. i followed the #3 and after typing "compiz --replace" my monitor goes blank. I reboot and relogin. After 5 second or some my monitor turn blank again, what should i do??

---

