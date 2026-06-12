---
title: "copying images to background folder"
date: 2010-11-20
forum: General Help
---

### Post by brunobliss on 2010-11-20
i know this is fairly easy to do so terminal using sudo, but i want to do it via graphical interface (for ease of access) but i can't write in the backgrounds folder because i don't have permissions to do so. although i made my account part of the administrators group and loged on again.

so basically, i need to have full control of my machine logged on with my user, i don't care about security at all. How?

---

### Post by ajgreeny on 2010-11-20
> i need to have full control of my machine logged on with my user, i don't care about security at all. How?Sorry to say this, but if you really mean it, you're mad!

There is no need to login as root to do anything in ubuntu; you can just open nautilus file manager for this one time with the command ```
gksudo nautilus
```in the Alt+F2 run dialog, but be careful; you can do great damage if you happen to remove or edit system files that should not be touched.

---

### Post by brunobliss on 2010-11-23
i do care about security, just not on my netbook, i can imagine that i'll have other sorts of problems like formating partitions and such using a graphical interface right?

---

### Post by lykeion on 2010-11-23
Maybe I'm misunderstanding your question, but why don't you just launch 
System > Preferences > Appearance > Background tab > Click Add button to add backgrounds.

---

### Post by deserthowler on 2010-11-23
get nautilus-gksu from the repos.  It adds a run as admin from the context menu.

Earl

---

### Post by lykeion on 2010-11-26
1. What backgrounds folder are you talking about? Is it /usr/share/backgrounds folder?
2. Why do you need to write to this folder? Is it to add a wallpaper manually?

To write to *any* folder as root user you can start nautilus with gksu as suggested in previous posts.

To change wallpaper there are better options:
* Use Appearence Preferences (as suggested in previous post)
* Install nautilus-wallpaper (with it you can right-click image and set as wallpaper in nautilus without need to run as root)

---

### Post by brunobliss on 2010-11-28
> **lykeion said:**
> Maybe I'm misunderstanding your question, but why don't you just launch 
System > Preferences > Appearance > Background tab > Click Add button to add backgrounds.

actually this simple trick will do it :) thanks


SOLVED

---

