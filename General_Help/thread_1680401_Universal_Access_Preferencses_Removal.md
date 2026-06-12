---
title: "Universal Access Preferencses Removal"
date: 2011-02-02
forum: General Help
---

### Post by uRock on 2011-02-02
**Ubuntu Version:** Ubuntu 10.10 AMD 64 (Desktop)

**Problematic Software:** Universal Access Preferences

**Symptom:** Universal Access Preferences is automatically starting and showing up in the Notification Area.

**How it started:** I tested out the magnifier applet, once.

**What I have done in attempt to fix the problem:** 
1. I opened Startup Applications, unticked and removed Universal Access.

2. I have uninstalled everything listed in the Ubuntu Software Center under Universal Access.

3. Rebooted.

4. Searched for a .conf in the /Home for this application.

**What I want from you:** Any ideas you may have for removing the Universal Access Preferences applet from the Notification Area, without removing the Notification Area.

**Edit;**
[COLOR=Red]**What I did to fix the problem:**[/COLOR] Opened gnome-keyboard-properties via Alt+F2, clicked the Accessibility tab, then unticked the "Accessibility features can be toggled with keyboard shortcuts" selection.

Thank you for any and all ideas,
uRock

---

### Post by Rubi1200 on 2011-02-02
Hi uRock,

I may have the solution for you:

Alt + F2 > gnome-keyboard-properties

Under Accessibility, uncheck the box  that says accessibility features can be toggled with keyboard.

(courtesy of forum member josephellengar)

Hope this helps.

---

### Post by uRock on 2011-02-02
Rubi1200,

You are awesome! That worked!

Cheers,
uRock

---

### Post by Rubi1200 on 2011-02-02
No problem, you are more than welcome :-)

---

