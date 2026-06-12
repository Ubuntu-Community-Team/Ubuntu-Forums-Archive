---
title: "user rights gone after logout"
date: 2010-05-26
forum: General Help
---

### Post by miles916 on 2010-05-26
hi everyone!

ive encountered a really weird problem today...

after my user had been logged out, i logged back in, and suddenly ive lost all manner of user privileges. all of a sudden my user cannot 
-mount drives (like my mp3 player or an external hdd)
-reboot the machine
-shutdown the machine
.
.

i checked users-admin (sudo) and all my rights are activated.
i installed pmount, thinking it was something to do with mounting drives...

all to no avail

many thanks in advance for any help

edit: after trying to open evolution, i noticed that i am not prompted to enter my keyring password, but single passwords for all my email accounts... could this be part of the problem?

edit2: i found this in log viewer:

```
May 26 20:46:24 Foundation gnome-keyring-daemon[7950]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified#012Autolaunch error: X11 initialization failed.
May 26 20:46:24 Foundation gnome-keyring-daemon[7950]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
May 26 20:46:25 Foundation gnome-keyring-daemon[7950]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
May 26 20:46:25 Foundation gnome-keyring-daemon[7950]: The SSH agent was already initialized
```

edit3: i guess it worked itself out automagically, because everything is back to normal this morning...

---

