---
title: "Keyboard volume controls (adjust change increment)"
date: 2011-05-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-05-11
Is there a way I can change the volume increase/decrees increments

---

### Post by TheNerdAL on 2011-05-11
I'm confused about what you mean by increments. You want to change which button can make the volume increase and which button can make the volume decrease?

---

### Post by pqwoerituytrueiwoq on 2011-05-11
it does what i want as it just i want to to raise/lower the volume a different amount
instead of raising/lowering volume by 10% raise/lower it by 5%

---

### Post by The__Doctor on 2011-07-25
Alt + F2 –> gconf-editor
Apps –> gnome_settings_daemon –> volume_step

Goto terminal, type gconf-editor. 
IN gconf-editor, goto gnome_settings_daemon.
Then click on gnome_settings_daemon and volume_step will appear in the right pane.

---

### Post by pqwoerituytrueiwoq on 2011-07-28
> **The__Doctor said:**
> Alt + F2 –> gconf-editor
Apps –> gnome_settings_daemon –> volume_step

Goto terminal, type gconf-editor. 
IN gconf-editor, goto gnome_settings_daemon.
Then click on gnome_settings_daemon and volume_step will appear in the right pane.
thanks

---

### Post by The__Doctor on 2011-08-01
no problem!

---

