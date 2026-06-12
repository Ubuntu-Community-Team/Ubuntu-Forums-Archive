---
title: "SAMBA not working properly?"
date: 2010-06-24
forum: General Help
---

### Post by Colo2 on 2010-06-24
I'm having great trouble networking my computers


Info:

______________
4 computers
- - - - - - -
3 are wireless
1 is hardwired
______________

2 are ubuntu, 2 are XP. 
ubuntu machine 1 has printers.
I managed to print a document from ubuntu machine 2 to ubuntu machine 1 via the network; however ubuntu machine 1's shared docs dont show up on any of the PCs.

I am unable to see ubuntu machine 1 on any of the windows pcs, cant find the printers or any sign of the PC actually being there, but pinging the PC is no problem.

Basically

network printing from ubuntu 2 to ubuntu 1 works fine; but ubuntu 2 cant see ubuntu 1s shareddocs and vice versa.

The windows PCs don't seem to even know that the ubuntu PCs exist. no printing or sharing


Stuck :( Help needed!!!

thanks.

---

### Post by Colo2 on 2010-06-24
Ubuntu 1 can see the 2 windows PCs
Ubuntu 2 can see itself and 1 of the windows PCs
(shared docs)

My network just seems to be absolutely screwed up

---

### Post by Colo2 on 2010-06-24
Please?

:( I don't want to have to take all these pcs back to windows.

---

### Post by Leppie on 2010-06-24
have you checked the workgroup names on your xp machines?
samba uses by default the name "WORKGROUP", but if you're running xp home your machines will be in another workgroup (don't recall the exact name right now).

---

