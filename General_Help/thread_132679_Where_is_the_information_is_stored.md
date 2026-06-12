---
title: "Where is the information is stored?"
date: 2006-02-18
forum: General Help
---

### Post by soongwoo on 2006-02-18
I' using Ubuntu 5.10.

When I do System -> Preferences -> Sessions from Tab menu "Startup Program" insert program "/usr/bin/run-this", then "run-this" is launched whenever I log in.

Where is the information stored? Normally, .bash_profile is the one.
But, I found forum article regarding it - not refering .bash_profile at session start.

Thanks
soongwoo

---

### Post by nanotube on 2006-02-18
afaik, that is stored in /home/username/.gnome2/session-manual
(where username is your actual username)

---

### Post by soongwoo on 2006-02-18
Thanks nanotube.

Does it mean I can put tasks in the file which are running at the beginning of session?

BTW, your customization document looks great.
I'm in the middle of setting Breezy, so it should give me lots of help.

soongwoo

---

### Post by nanotube on 2006-02-18
hey
well you really should not have any reason to edit that file directly - you can add or remove tasks from the session control panel.

but yes, those tasks are ones that would start up when you log into gnome.

glad you like my howto. :)

---

