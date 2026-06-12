---
title: "gnomenu shutdown button"
date: 2010-03-30
forum: General Help
---

### Post by panti19 on 2010-03-30
when i click the shutdown button in gnomenu it displays the log out of the session  screen with only log out and switch user as options.
i have another ubuntu machine downstairs with gnomenu and the same theme installed but it displays the shutdown screen.
how do i change that? thanks

figured it out myself :D

---

### Post by anantshri on 2010-03-31
care to share

---

### Post by panti19 on 2010-03-31
in gnomenu properties
commands
shutdown dialog: instead of gnome-session-save --logout-dialog
write gnome-session-save --shutdown-dialog

---

