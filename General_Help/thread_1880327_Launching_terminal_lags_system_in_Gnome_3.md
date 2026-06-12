---
title: "Launching terminal lags system in Gnome 3"
date: 2011-11-13
forum: General Help
---

### Post by kedmond on 2011-11-13
Hey everyone,
  I'm running Ubuntu 11.10 and I installed Gnome 3.  When using Gnome 3, launching the terminal causes a 3 second lag before the terminal launches.  The system actually just completely freezes and is unresponsive until the Terminal launches.  This lasts 2-3 seconds each time, and then resumes normal operation.

This does not happen in Unity.  Anyone else run into this?


UPDATE: I removed Compiz and there's no longer any lag.  However, there's lag whenever it does a search.  Shouldn't all of my metadata be cached?

UPDATE 2: OK, nevermind, the lag is back.  I have no idea what's going on....

---

### Post by pjbp on 2011-11-14
I have also experienced problems with Gnome 3 on Ubuntu 11.10.  In particular, when I begin typing in the terminal window there is often a long lag before what I typed shows up in the window.  Also, parts of the terminal window will go blank after I start typing until I hit enter a few times or wait a few seconds.  It is an incredibly annoying problem and has forced me back to Unity which I find unfortunate because I think Gnome 3 overall is a very intuitive interface.

---

### Post by kedmond on 2011-11-14
> **pjbp said:**
> I have also experienced problems with Gnome 3 on Ubuntu 11.10.  In particular, when I begin typing in the terminal window there is often a long lag before what I typed shows up in the window.  Also, parts of the terminal window will go blank after I start typing until I hit enter a few times or wait a few seconds.  It is an incredibly annoying problem and has forced me back to Unity which I find unfortunate because I think Gnome 3 overall is a very intuitive interface.



Yeah, I get strange lags like that too...however, they're becoming more and more infrequent.  They're intermittent at best...which makes them really hard to diagnose.

I get the most significant and consistent lag (100% of the time) when I perform any kind of search.

---

### Post by tbone7 on 2012-01-06
I can confirm what the op wrote in the first post. Launching the terminal freezes the my 64-bit 11.10 system for approx. 2 seconds before it pops up. From there it seems to run as normal at my system, but I haven't done much testing.

---

### Post by collisionystm on 2012-01-06
I am sure that if you run htop in terminal you will see that compiz is always the top of the list.

I had the same problem until I disabled Sync to Vblank in OpenGL ( from the compiz config ). However, from what I have seen on my machine, you cannot disable sync to vblank while using gnome shell. Only Unity.

---

### Post by kedmond on 2012-01-10
> **collisionystm said:**
> I am sure that if you run htop in terminal you will see that compiz is always the top of the list.

I had the same problem until I disabled Sync to Vblank in OpenGL ( from the compiz config ). However, from what I have seen on my machine, you cannot disable sync to vblank while using gnome shell. Only Unity.

I don't think that I have compiz installed.  I'm just using Gnome 3...unless Compiz is somehow magically built in.

---

### Post by jerrrys on 2012-01-10
I had this lag problem back in 11.10 testing days.  And as a work-a-round I installed "lxterminal", this made a big difference in my box.

Presently, gnome-terminal is fast.  I wonder if it has anything to do with installing "preload"...

---

