---
title: "Maximus???"
date: 2009-09-05
forum: General Help
---

### Post by Gabt on 2009-09-05
What is it? Everytime i close a window i get about 30 "opening maximus" things in my 'taskbar' . Very annoying. How do i get rid of it?

---

### Post by coldReactive on 2009-09-05
[From Wikipedia]("http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix#Packages_That_Make_Up_UNR"):

> **maximus** 
    A window-management daemon (makes sure windows are maximized etc)

---

### Post by winotree on 2009-09-05
Seems like Maximus [http://www.freesoftwaremagazine.com/columns/ubuntu_netbook_remix_detailed_explanation](http://www.freesoftwaremagazine.com/columns/ubuntu_netbook_remix_detailed_explanation) is part and parcel to your distribution.  I've read (although I can't point you to it just now) that it (Maximus) can be removed via Synaptic Package Manager -- although I can't Imagine what you'd have after that...  :?

---

### Post by bodhi.zazen on 2009-09-05
You can either remove maximus or disable it.

Find your maximus .desktop files (I forget where they are, there are two).

change the Exec line to

Exec maximus -s -m

You can then kill maximus (otherwise it re-starts).

See man maximus.

---

### Post by Gabt on 2009-09-05
Hmmm, i like the way it maximizes windows too(useful on 10" displays), but its obviously flawed.

---

### Post by bodhi.zazen on 2009-09-05
> **Gabt said:**
> Hmmm, i like the way it maximizes windows too(useful on 10" displays), but its obviously flawed.

yes, it is a bit buggy yet, it works most of the time, which is why you may not wish to remove it, rather use some options such as -s , -m or see man maximus.

---

### Post by Gabt on 2009-09-05
Having a play around with it now.

---

### Post by Gabt on 2009-09-05
-m removes my window borders, no close buttons etc now.

Ill just ahead and remove it.

---

