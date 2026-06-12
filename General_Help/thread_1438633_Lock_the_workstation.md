---
title: "Lock the workstation"
date: 2010-03-25
forum: General Help
---

### Post by pix3l on 2010-03-25
Good afternoon,

In order to acheive a Bluetooth remote control application I wanted to know if it's possible to Lock the workstation on ubuntu as we do on Windows with the following command :
rundll32 user32.dll,LockWorkStation

If there's a possibility, what's the appropriate command line for such operation?

Thanks

---

### Post by new_tolinux on 2010-03-25
I guess this is what you're looking for.

```
gnome-session-save --logout-dialog
```

source: [http://ubuntuforums.org/showthread.php?p=8041957#post8041957](http://ubuntuforums.org/showthread.php?p=8041957#post8041957)

---

### Post by seanUSXIII on 2010-03-25
I'm using:

```
gnome-screensaver-command --activate
```

on the blueproximity locking app, you just have to make sure that you have the screensaver set to lock the screen when it comes up

---

### Post by pix3l on 2010-04-02
Thank you. This is exactly what i'm looking for.

---

