---
title: "Password prompt on resume - gconf setting ignored"
date: 2010-10-10
forum: General Help
---

### Post by enray on 2010-10-10
Is there some extra configuration required to disable the password prompt in UNR?

I am trying to disable the password prompt on resume from standby/hibernate. I have cleared all the locks in gconf-editor/apps/gnome-power-manager/locks, screensaver is also cleared, I've sudo'ed gconf-editor, everything looks like I believe it should but the prompt remains each time the machine resumes. 

Starting from cold the machine logs me in without a password, this is only a problem on resume. I am using the default UNR theme, the only change I made was to enable extra workspaces in gconf... out of ideas what to try next.

---

### Post by Quackers on 2010-10-10
Try checking the box "use screensaver settings" in gconf-editor (if it isn't already).

---

### Post by enray on 2010-10-10
Thanks Quackers, just tried that and no change. If I choose "Switch User" on the password prompt I can then click my user name and come right in without a password - could it be the "Switch User" or the "Leave Message" function which is popping up the login box, rather than the password requirement? Is that something I can disable?

---

### Post by Quackers on 2010-10-10
Did you check in System > Preferences > Screensaver that "lock screen when screensaver is active" is unchecked?

---

