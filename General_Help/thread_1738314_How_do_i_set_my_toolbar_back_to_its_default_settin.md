---
title: "How do i set my toolbar back to its default settings?"
date: 2011-04-24
forum: General Help
---

### Post by El3mentGamer on 2011-04-24
I accidentally screwed it up.

---

### Post by Horseboy on 2011-04-24
> **El3mentGamer said:**
> I accidentally screwed it up.

We cannot help if you don't supply enough information. What version of Ubuntu are you running? Gnome 2 or 3? And what do you mean by "screwed up"?

---

### Post by KegHead on 2011-04-24
Hi!

Try this if in 11.04;

system...admin...login..

Select "xxxx" as default.

KegHead

---

### Post by El3mentGamer on 2011-04-24
I apologize. Im running Ubuntu 10.10 and i delete the default chat icon, the default email icon, and so forth. I know i can add the application launchers, but they dont act the same as the defaults

---

### Post by Toolless on 2011-04-24
when i did **** like that in windows i just rebooted the pc from the windows insulation CD and went into the reapair modual 
kind of delited and re installed system files automatically

---

### Post by Krytarik on 2011-04-24
Just run these commands in a terminal:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```If you have no direct access to one, press Ctrl+Alt+T to launch one.

Or press Alt+F2 to get the (panels') 'Run' dialog.

Greetings.

---

### Post by El3mentGamer on 2011-04-24
Thanks Krytarik! It worked! Kudos to you!

---

