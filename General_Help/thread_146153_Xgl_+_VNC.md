---
title: "Xgl + VNC"
date: 2006-03-17
forum: General Help
---

### Post by razialx on 2006-03-17
I switched back from Dapper to Breezy, and setting up Xgl was simple.

However, since I have set it up, I can no longer VNC into the computer.
In fact, if I try to use vncviewer in Ubuntu to connect to itself, it crashes out (the viewer, not Ubuntu).

Now, I have tried connecting before running Compiz (thefuture) and after, and I get the same results.

From Windows, using TightVNC or UltraVNC I get the error message "Socket Read error:" ... I will try to get the exact message up when boot my laptop back up. 

It just seems strange, and I was wondering if anyone else has had problems with this odd combination.

I will be honest, I just really want to see floppy windows in Windows, hehe.

Any help is greatly appreciated.

(Do you think it has to do with the screen name config, which was :
0 = Screen
and is now
0 = Xgl
???
And that I may have to change something in the VNC server's config files?
and if so, where would those config files be?)

Thanks!
razialx

---

### Post by razialx on 2006-03-18
No thoughts, experiences? 

:cry:

---

### Post by cbudden on 2006-03-18
Same problem with me.

---

### Post by Tao on 2006-03-22
Same problem with VNC.
A solution is to use FreeNX, there is no problem with XGL. In addition, it is faster than VNC, but we cannot resume a session (or I don't know how).

---

### Post by steve31783 on 2006-03-22
which set of directions did u follow to get xgl working in breezy "easily" ?

---

### Post by JackandJohn on 2006-05-05
I'm not sure what would lead you to beleive that this was something feasible..

VNC is a way of viewing your screen remotely; it *basically* takes a picture and transferrs it across.

XGL draws your screen on the graphic card, and thus lets you do all these fun graphical things.


Basically what you are asking the computer to do is remotely draw it on the graphic card: Kind of like calling someone and expecting to watch HDTV through the phone just because they have one.

NX doesn't load xgl when it runs, therefore it's not going through the same process.

---

