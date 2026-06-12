---
title: "Switch display to external monitor with laptop lid closed"
date: 2010-12-23
forum: General Help
---

### Post by superchargedtoaster on 2010-12-23
I don't know if it sounds weird but I've been trying for weeks with no result. I want to plug my external monitor through my laptop's vga plug, close the lid and work on my monitor instead of the laptop's monitor. I looked through the gnome power management settings and when the laptop lid is closed it can only suspend, blank screen, hibernate or shutdown. I can plug my monitor and I have clone displays and it works fine but I can' find a way to shutdown the laptop screen without shutting down the vga outlet. Its a brand new Acer aspire 5734Z with a 15,6 inches screen (wich is why I want to plug in my 19 inches monitor and work on bigger screen)
Thank you

---

### Post by Habitual on 2010-12-23
What version of Ubu is this?

Here's what I have and mine works:

"On AC Power"
Never
Do nothing
Never
**de-select** all checkmark boxes

"On Battery Power" tab:
Never
Blank Screen
Shutdown
Never
and **de-select** all checkmark boxes

Under Monitors (Prefs) make sure laptop is set to "Off".

HTH.

---

### Post by superchargedtoaster on 2010-12-24
Good for you, but I don't have your luck, I'm on 10.10 and in the power management there is no option "do nothing". I can manage to shut down the laptop screen and use the monitor but whatever I do, when I close the lid both screens become blank or it suspends or hibernates or shutdown.
Thank you, again  and merry Christmas by the way

---

### Post by superchargedtoaster on 2010-12-26
I fixed it, I went in gconf-editor and changed the lid_ac setting to nothing

---

