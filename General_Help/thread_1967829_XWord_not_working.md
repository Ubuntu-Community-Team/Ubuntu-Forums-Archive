---
title: "XWord not working"
date: 2012-04-28
forum: General Help
---

### Post by gpguitarman1 on 2012-04-28
I just upgraded to Ubuntu 12.04 and Xword will not open any puzzles. I saw a thread for a fix,  [https://bugs.launchpad.net/ubuntu/+source/xword/+bug/875451](https://bugs.launchpad.net/ubuntu/+source/xword/+bug/875451), but I'm not sure exactly what to do. A step by step guide will be very helpful. 

Thanks in advance,
Gary

---

### Post by gpguitarman1 on 2012-04-30
I got it working.. thanks from [Aaron Sarna (shoofy)]("https://launchpad.net/%7Eshoofy")                                     As lykwydchykyn wrote above, you should open up /usr/games/xword in your favorite editor and replace line 314, which should be:
m = md5.new()
with:
m = md5()
and then save it.
 One way to do that would be (from a terminal):
gksu gedit /usr/games/xword
type in your password when prompted
press ctrl+i and type 314 and press enter (this should take you to the line at fault)
replace that whole line with: m = md5()
press save
Now try opening your puzzle again.

---

### Post by kdrainey on 2012-06-20
Thanks, this worked, but xword still seems a bit buggy.  After I applied the fix the first time, worked a bit of a puzzle, saved and quit, xword would not restart.  I reinstalled and reapplied the fix.  Now it will restart from the DASH, but it locks into Unity bar as a ghost.  It is there, but is a blank space in the bar. Clicking on the blank space will restart xword.

---

