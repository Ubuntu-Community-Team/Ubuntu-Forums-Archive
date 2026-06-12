---
title: "loggon help (GUI)"
date: 2006-03-29
forum: General Help
---

### Post by pokerface on 2006-03-29
every time i log in using the GUI it says in a bubble ```
your $HOME/.dmrc has incorrect permissions and is being ignored. This pervents the default session and lanuage from being saved. File should be owned by user and have 644 permissions.
``` anyone know how i could put those permissions back?
or how to fix this in anyway?

---

### Post by aysiu on 2006-03-29
Reboot and select recovery mode (the one above memtest and below the regular Ubuntu).

This should boot you into root mode.

Type ```
chmod 644 /home/pokerface/.dmrc
```

Then try rebooting normally and log in as pokerface.

---

### Post by pokerface on 2006-03-29
it didnt seem to work! i did what u said but it still gave me that bubble with that warning! any other ideas?

---

### Post by aysiu on 2006-03-29
[QUOTE=pokerface]it didnt seem to work! i did what u said but it still gave me that bubble with that warning! any other ideas?[/QUOTE] Well, the warning said it's either that it's not owned by you or has the wrong permissions. That command changes the permissions. Maybe what we need to do is change the owner, too: ```
chown pokerface:pokerface /home/pokerface/.dmrc
chmod 644 /home/pokerface/.dmrc
```

---

### Post by pokerface on 2006-03-30
sorry, but that didnt work either! i still get it after i rebooted my computer and signed in!

---

