---
title: "It wont boot! i think i killed it..."
date: 2009-07-07
forum: General Help
---

### Post by Blender3d on 2009-07-07
ok, so i was using ubuntu for like a week. yesterday at like 1 in the morning, i started it up and it booted to the graphical login screen, but before the log in prompt could come up, it cuts to a black screen with an X shaped cursor...WHY! what did i do? 

no prompt or anything, I cant even fix it...unless i go into safemode er whatever...

---

### Post by Megrimn on 2009-07-07
can you move the cursor?

[edit] try this:

boot into the GRUb menu, where you have all of your boot options displayed:

Highlight the line that boots into Ubuntu, and press 'e' on your keyboard.

after that, highlight the 'root' line and hit 'e' again

add 'xforcevesa' to the end of that line, hit 'enter', then press 'b' on your keyboard.

this change is not permanent, so if it doesn't work, you don't have to fix it.




If that works, then you are having a graphics driver problem.

---

### Post by Blender3d on 2009-07-07
I can move the cursor, it just doesnt do anything, its just a white x. and this happened right *before *i installed nvidia gfx drivers, it didnt help.

---

### Post by CatKiller on 2009-07-07
As a wild stab in the dark, it sounds to me like GDM isn't starting. Are you able to switch to a virtual console with Ctrl-Alt-F1? If you are, what happens if you run ```
sudo /etc/init.d/gdm start
```(If it doesn't change automatically, Alt-F7 will take you back to the graphical environment)

---

