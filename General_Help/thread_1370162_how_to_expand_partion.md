---
title: "how to expand partion?"
date: 2010-01-01
forum: General Help
---

### Post by epablo on 2010-01-01
g'day & a happy new year  forum...
    ..i installed ubuntu from windows xp into drive d: which i had emptied. the drive has over 100 gigs of space. the partition  that was created by the installer was 4 gigs. i have tried to expand that 4 gigs to at least 50 but no program that i have tried will allow me to expand beyond the 4 gigs. i was wondering can it be done and if yes how? sorry if this question has already been answered. i searched and couldn't find.
with appreciation
    epablo

---

### Post by Pesky_Programmer on 2010-01-01
Try typing "sudo apt-get install gparted" without the quotes into a terminal window. This will install gparted, a tool for partitioning, into ubuntu.You should also be able to find this from the software center in ubuntu as well.

Once installed choose go to system->administration->partition editor

I will assume you have used a partitioning program if not you can read the documentation that comes with gparted it is pretty straight forward. 

Just be careful you don't accidentally delete something important in the process.

I hope this helps :).

oops I misunderstood Ignore my post for now but if you do a full install later gparted is a must.

---

### Post by HappyFeet on 2010-01-01
A proper install of ubuntu would allow you to use the whole drive, or as much as you want. Plus, a real install of ubuntu will give you better performance.

What you have done is called "wubi", which is basically running ubuntu inside of xp, instead of on its own. Just some food for thought. Since you seem to like ubuntu, a regular install would be much better.

---

### Post by epablo on 2010-01-02
> **HappyFeet said:**
> A proper install of ubuntu would allow you to use the whole drive, or as much as you want. Plus, a real install of ubuntu will give you better performance.

What you have done is called "wubi", which is basically running ubuntu inside of xp, instead of on its own. Just some food for thought. Since you seem to like ubuntu, a regular install would be much better.

..thank you. because of the laptop i use i would do better with remix so it's looking more like i'll need to do a "real" install though i hate for all the effort i already put into setting things up go to waste........epablo

---

