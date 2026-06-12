---
title: "Okay, so i hate mutter. how do i get compiz back?"
date: 2010-10-13
forum: General Help
---

### Post by Atamisk on 2010-10-13
As the title suggests, i despise the new wm in ubuntu netbook, mainly because i can't do all of my cool tricks, like my cube and my other compiz effects that i've grown accustomed to. 

So how do i roll back to the old netbook remix interface? i left the package there, i just need to know how to enable it.

---

### Post by WorMzy on 2010-10-13
I've never used this "remix" version of Ubuntu, but can you not just install Compiz and run
```
compiz --replace
``` to use it instead of mutter? That's all it'd take on a standard Ubuntu installation.

---

### Post by Atamisk on 2010-10-13
you'd think, but no, it freaks the system out and i end up with NO wm...

---

### Post by sikander3786 on 2010-10-13
Logging out and selecting Gnome under Sessions should help.

---

### Post by Atamisk on 2010-10-13
you're right, it should. but for some reason, anywhere i go, i can't get the alt-f2 dialog to come up. is there a terminal command for the binary that runs when alt-f2 is pressed?

---

### Post by Atamisk on 2010-10-13
Clarification: 

If i force replace mutter with compiz, the whole Unity interface goes away and i'm left with nothing. I i go into UDesktop, compiz works fine. However, if i wanted to use the desktop version of ubuntu, i wouldn't have installed UNR, so this, to me, is a NON-solution. 

Is there a way to bypass unity and return to the old UNR interface??

---

### Post by Atamisk on 2010-10-13
I answered my own question, and the answer is no. The old launcher is obliterated when UNR is upgraded (they use a "Transitional Package" that replaces/renders useless the binary.), and compiling it from the source on launchpad is less than possible because 10.10 has package naming differences that are a pain for the average user to overcome. :(


I am GOB SMACKED that Ubuntu's developers offer UNR users NO CHOICE but Unity for the interface.

(btw, would compiling the source for netbook-launcher in 10.04 using checkinstall make a usable package?)

---

### Post by punong_bisyonaryo on 2011-03-06
Following this thread, I also would like to know how to get Compiz running with 10.10 UNE. Though I think the Unity interface is kinda spiffy too.

I read that 11.04 is coming out with Compiz as the default for Unity.

---

