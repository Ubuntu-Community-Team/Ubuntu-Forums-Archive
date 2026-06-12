---
title: "Live CD not working"
date: 2006-02-23
forum: General Help
---

### Post by PowerJC on 2006-02-23
I booted up the live cd and got a X windows system error.  I have amd athlon 64 3800+ x2 dual core and a x800gt graphics card.  Please help *** i really want to try linux.  P.sS i was able to get damn small linux working earlier.

---

### Post by lamego on 2006-02-23
Do you get a terminal console ?
Check the contents of /var/log/Xorg.0.log for some more details...

---

### Post by PowerJC on 2006-02-23
It justs hangs.  Its an ati graphics card but found a work around on another page going to try it and will post with the results

---

### Post by PowerJC on 2006-02-23
Got it working.

---

### Post by rjwood on 2006-02-23
How did you get it working? I have a friend who wants to install breezy on a computer he made. It's an amd 64 3500. It does not have anything installed. The live cd begins to install and then message appears that say's he needs intel based system then just turns into different colors and freezes.

---

### Post by redwings0921 on 2006-02-23
happened to me, just throw that disc away and the do the process all over again, worked with me

---

### Post by PowerJC on 2006-02-25
It was to do with my graphics card switched it to vesa and it worked ok

---

### Post by Ramses de Norre on 2006-02-25
I have got the same problems, I changed the graph driver to vesa from shell so I could use X. Then installed the fglrx drivers and changed the graph driver to fglrx.
Didn't have any problems with it ever since.

---

