---
title: "Installing over Windows vs Normal Install"
date: 2012-09-10
forum: General Help
---

### Post by Kocrachon on 2012-09-10
So normally when I install ubuntu, I do a normal install by making its own partition and installing it that way. However, I was starting to think about doing the install ontop of windows.

What are the advantages of this? Or disadvantages?

---

### Post by GreatDanton on 2012-09-10
What do you mean to install it on top of Windows. Wubi installer?

---

### Post by Kocrachon on 2012-09-10
> **GreatDanton said:**
> What do you mean to install it on top of Windows. Wubi installer?


Yes sorry, when you install it within windows itself.

---

### Post by offgridguy on 2012-09-10
One advantage is, it is easier to uninstall if you decide to later as they both use the same disk 
space.  As to disadvantages, why open one OS to run a different one?

---

### Post by jerome1232 on 2012-09-10
> **offgridguy said:**
> .  As to disadvantages, why open one OS to run a different one?

I think you're a little confused about how wubi works, it doesn't load Windows and then load Wubi. Rather it simply uses a virtual file-system on top of the windows c:/ partition.


The disadvantages are slightly slower disk access times, and an easily corrupted files-system, since you have a file-system on top of a file-system. Wubi was never meant for long-term use, it's just an extended test for those who aren't sure if they want Ubuntu so that they can install it without repartitioning.

---

### Post by offgridguy on 2012-09-10
Thank you for the clarification.

---

