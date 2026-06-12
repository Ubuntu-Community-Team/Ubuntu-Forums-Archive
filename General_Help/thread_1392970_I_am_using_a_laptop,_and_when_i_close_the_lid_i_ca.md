---
title: "I am using a laptop, and when i close the lid i cant log back in?"
date: 2010-01-28
forum: General Help
---

### Post by 006ruler on 2010-01-28
I'm completely lost. It used to be that when i closed the lid of my laptop and it went to sleep, when i opened the laptop again it had the logon scree. Now when i open the laptop, it just goes from the "off looking" screen to the grayer black screen. I'm forced to press and hold the power button until it shuts down, then restart my computer. Does anyone have any suggestions?

And i have left it alone for a while on the gray scree, and it just stays gray, never changes.

---

### Post by raktarok on 2010-01-28
I don't know if you tried this, but can you switch to one of the virtual consoles? Press Ctrl+alt+f1 (or f2, f3...) login and then issue this command:
```

sudo /etc/init.d/gdm restart
```

See if you have gnome running. Switch to ctrl+alt+F7 if nothing happens, and see if there's any change.

This is not going to solve the problem, but at least we will know if things work...

---

