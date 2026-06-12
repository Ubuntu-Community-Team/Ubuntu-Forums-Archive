---
title: "computer freezing"
date: 2011-10-13
forum: General Help
---

### Post by comradeluigi on 2011-10-13
for few days now my computer has been freezing and the screen gets all messed up
like this
 
im running ubuntu 11.04 [IMG]http://img194.imageshack.us/img194/1879/111eyk.jpg[/IMG]

---

### Post by Mark Phelps on 2011-10-13
Freezing is often caused by excessive heat -- a problem known to affect the 11.x Ubuntu versions.  Since you're getting a display issue, and your PC is not shutting down, my guess would be that your GPU is running hot.

What you can try, since this appears to be a desktop PC, is opening the case and spraying compressed air into the fan slots for your video card.  Also do that to the CPU heat sink fins.

---

### Post by ultrageeky on 2011-10-13
Completely remove then reinstall your display driver.

Have you changed any display settings such  as Emerald or Compiz desktop effects? Try lowering the number of effects in use or remove Compiz and Emerald - I don't like them anyway ;)

You can check for CPU overheating by loading your computer into its BIOS setup screen and leaving it running overnight. If it freezes in the BIOS then it's overheating. Freezing in the BIOS screen proves the fault to not be OS related and so will narrow your scope for finding its cause.

Edit to add: when it freezes, can you press Ctrl+Alt+F1 to drop to a shell? What happens when you press Ctrl+Alt+Del?

---

### Post by comradeluigi on 2011-10-13
> **ultrageeky said:**
> Completely remove then reinstall your display driver.
 
Have you changed any display settings such as Emerald or Compiz desktop effects? Try lowering the number of effects in use or remove Compiz and Emerald - I don't like them anyway ;)
 
You can check for CPU overheating by loading your computer into its BIOS setup screen and leaving it running overnight. If it freezes in the BIOS then it's overheating. Freezing in the BIOS screen proves the fault to not be OS related and so will narrow your scope for finding its cause.
 
Edit to add: when it freezes, can you press Ctrl+Alt+F1 to drop to a shell? What happens when you press Ctrl+Alt+Del?
 it doesn't  freeze while i'm not using it

---

### Post by ultrageeky on 2011-10-13
Usually when a computer overheats it will just switch off after a while of being frozen. As Mark said, your graphics adapter might be overheating but I still suspect a software issue. Does it happen when you use a live disc?

---

### Post by comradeluigi on 2011-10-13
> **ultrageeky said:**
> Usually when a computer overheats it will just switch off after a while of being frozen. As Mark said, your graphics adapter might be overheating but I still suspect a software issue. Does it happen when you use a live disc?i think it is a software problem, i can still move the mouse, i'll try a live cd to see if it still happens

---

### Post by ultrageeky on 2011-10-13
I apologize for my late replies, I've been busily working away between visits.

Run this command when your desktop is running normally and post the results here:

```
egrep '\(EE\)|\(WW\)' /var/log/Xorg.1* | less
```If the Live Disc works flawlessly, test the conditions of your desktop environment by reloading your PC without the Live Disc and creating a new user (do not log in just yet):

[LIST]
[*]drop to a shell by presing Ctrl+F1
[*]type "sudo adduser username" (change "username" to a new username)
[*]press enter
[*]enter your login password
[*]follow the prompts.
[/LIST]
Once the new user has been created, press Ctrl+F7 to restore the graphical login prompt then login as the new user.

The new user should have a clean desktop environment with fewer/no configuration options that might cause your OS to play up.

---

