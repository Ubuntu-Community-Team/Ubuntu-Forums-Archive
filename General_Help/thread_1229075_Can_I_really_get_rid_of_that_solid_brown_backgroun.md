---
title: "Can I really get rid of that solid brown background?"
date: 2009-08-01
forum: General Help
---

### Post by DGeeez on 2009-08-01
While I kinda like the Ubuntu "Human" theme with red, orange, and yellow, my opinion on brown is that it requires a lot more finess than has been applied to the brown backgrounds, and that lack easily makes the difference between really beautiful and disgusting. But there is something worse than that Rorshach test of a default background - it's that SOLID, diarrhea-colored background which is the other of two options in a new Ubuntu install! It turned out to be inexorable somehow. It wouldn't be so annoying if it weren't so hard to avoid, but it appears in the upper-left-hand corner of my System->Appearances->Background tab, and the system won't allow me to remove it (why)! I've had to manually change the solid backgrounds behind each of my background photos in that tab, but every time the system restarts the brown flashes before the black (or whatever color I selected to go behind my background image) solid backround comes on, followed by my background picture, and I'm like what the hell for? It wouldn't bother me so much if it was a nicer color, or if I could rationalize this system behavior. Why should more than the solid background fill color and the image which I selected, at startup? Can anybody help with this?

---

### Post by CatKiller on 2009-08-01
System &#8594; Administration &#8594; Login Window &#8594; Local &#8594; Background colour.

---

### Post by MaxIBoy on 2009-08-01
> **CatKiller said:**
> System &#8594; Administration &#8594; Login Window &#8594; Local &#8594; Background colour.
That's actually no longer there in 9.04. You have to do this:
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename "/insert/name/of/background/picture/file/here"
```

---

### Post by DGeeez on 2009-08-02
> **CatKiller said:**
> System &#8594; Administration &#8594; Login Window &#8594; Local &#8594; Background colour.

CatKiller, you're a god! If you happen to be looking for more cats to kill, I'll gladly sacrifice mine to you:D:D

Seriously, that path works, and my system is actually is 9.04 - can't remember if I upgraded from Intrepid, how or if that's possible (my sanity requires frequent blackouts of time spent moving files for newer system installs). Anyway, my system looks so sharp right now, that I'd have to pay somebody for it if it installed like this out of the box.

Thanks!

---

### Post by CatKiller on 2009-08-02
> **MaxIBoy said:**
> That's actually no longer there in 9.04. You have to do this:
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename "/insert/name/of/background/picture/file/here"
```

I think you're confused. The OP is changing the background **colour** of the GDM login, which shows for a while after the login window disappears and before the desktop appears. Your solution changes a background **image**.

---

### Post by DGeeez on 2009-08-02
> **CatKiller said:**
> I think you're confused. The OP is changing the background **colour** of the GDM login, which shows for a while after the login window disappears and before the desktop appears. Your solution changes a background **image**.

Well, the brown background at the login has been replaced with what I want, but it's still forcibly taking up space in my Appearance Preferences->Background window. Would Maxi's fix get rid of that?

---

### Post by CatKiller on 2009-08-02
No. The background for the login window and for the desktop are different settings (although you could set them to the same value). You can change the arrangement of the background image on the Desktop with the Style drop-down box. Zoom or Fill screen will eliminate the background colour from showing round the outside. The others won't, necessarily.

---

