---
title: "Screen goes black"
date: 2010-09-22
forum: General Help
---

### Post by SoAb on 2010-09-22
in ubuntu 10.04 i have compiz installed and when i try to rotate the cube or simply change desktops screen goes black but not entirely,i mean i can still see the cube..this happens only during the change of desktops.Its very annoying,it doesnt create trouble but i cant see the cube effect.Help :D

---

### Post by migs73 on 2010-09-22
Hi, I'm not on my ubuntu machine right now so the naming might be a bit off here, but;
Try check your compiz settings. The cube background (Skydome) may be set to be black and the opacity settings for the cube itself may be letting you see straight through it or almost ("goes black but not entirely").

---

### Post by SoAb on 2010-09-22
i didnt have skydome but now now that i activated it only the cube goes black... here's a pic [[IMG]http://img227.imageshack.us/img227/238/screenshot2v.png[/IMG]](http://img227.imageshack.us/i/screenshot2v.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by linux-hack on 2010-09-22
the problem can come from the compiz configuration but also from the graphic card. Try reconfiguring compiz and if nothing changes try updating or reinstalling you graphic drivers. but backup everything before doing this.

---

### Post by SoAb on 2010-09-22
this is weird stuff...now it doesnt go so much black i can see everything its like its shaded o.O and that happens when i zoom with super key and middle mouse button

---

### Post by migs73 on 2010-09-22
You probably have a few too many compiz effects running for your graphics card to cope. Try switching off the 3D windows and switching off your widgets. If that works you have some choices to make!

---

### Post by SoAb on 2010-09-22
i have almost all effects off...i dont think that is the problem..in 9.10 compiz was running perfectly with many effects.I think that its an option in 10.04 to shade it like that or a bug.

---

### Post by pelotin on 2010-11-12
Bump for justice! I have the same problem, could you solve that?

---

### Post by exodeos on 2010-12-28
not meaning to resurrect an old post but I found a "fix" by accident. I installed the compiz experimental plug ins ([http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32%2664+NEW+!?content=118511](http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32%2664+NEW+!?content=118511)) and used the "snowing" effect. After playing around with this for a while I switched desktops and noticed it didn't go dark which was unusual for me so I enabled desktop cube and rotation and whenever the snow, fireflies, or stars effect is on, the screen does not go dark when rotating (admittedly there is a very small moment where it does but it does not stay) I set my star effect to have zero stars and now have rotation without having to see the star effect. I have no idea whatsoever why this worked but thought I would post it here to help those with my old problem, and in the hopes that someone who can find out sees this.

---

### Post by DMJ on 2011-03-12
See this old 2007 forum post: [http://forum.compiz.org/viewtopic.php?t=5444&f=116](http://forum.compiz.org/viewtopic.php?t=5444&f=116)

The answer is to uncheck ccsm>display settings>lighting

Note that in openSUSE 11.4 the option is in ccsm>openGL. Probably a newer version. I had this problem on my Dell Inspiron 8500 for both Suse and Mint, but not on my desktop. This fixed it on both. Strange this is still an issue after so many years. Graphics card is ATI radeon 9000.

---

