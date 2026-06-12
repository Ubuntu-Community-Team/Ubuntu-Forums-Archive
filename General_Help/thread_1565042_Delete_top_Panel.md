---
title: "Delete top Panel?"
date: 2010-08-31
forum: General Help
---

### Post by Cam! on 2010-08-31
I don't have a need for any panels anymore, and I'm unable to delete the primary panel that came with Ubuntu. How do I delete it?

---

### Post by M93 on 2010-08-31
> **Cam! said:**
> I don't have a need for any panels anymore, and I'm unable to delete the primary panel that came with Ubuntu. How do I delete it?

hers's ur answer
[http://ubuntuforums.org/showthread.php?t=652367](http://ubuntuforums.org/showthread.php?t=652367)
;)

---

### Post by ean5533 on 2010-08-31
> **Cam! said:**
> I don't have a need for any panels anymore, and I'm unable to delete the primary panel that came with Ubuntu. How do I delete it?

If you're replacing it with another panel, such as AWN, you can follow the instructions on [this link]("http://wiki.awn-project.org/FAQ#How_do_I_set_up_GNOME_session_to_start_Awn_instead_of_GNOME_Panel.3F").

If you just want to prevent gnome-panel from starting up at login, try running this in a terminal:

```
gnome-session-remove gnome-panel
```

Be careful, as that will (I believe) also remove the Alt+F2 run dialog, which is a part of gnome-panel.

---

### Post by limestone on 2010-08-31
If you want to run without panels you could use another window-manager eg.
openbox, pekwm, wmaker or other. And simply choose that session when logging in.

---

