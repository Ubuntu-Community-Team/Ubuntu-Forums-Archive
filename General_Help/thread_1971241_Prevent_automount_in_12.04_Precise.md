---
title: "Prevent automount in 12.04 Precise?"
date: 2012-05-02
forum: General Help
---

### Post by Paddy Landau on 2012-05-02
In Natty, I could prevent the system from automounting devices (such as USB flash disks and USB hard drives) when plugged in, using
gconf-editor > /apps/nautilus/preferences > media_automount

But, that item no longer exists in 12.04.

How can I prevent 12.04 from automounting devices?

---

### Post by mc4man on 2012-05-02
It's in gsettings, (dconf-editor which is in the dconf-tools package

schema is org.gnome.desktop.media-handling, key is automount, see screen (edit - replaced screen with correct key highlighted

from cli
```
gsettings set org.gnome.desktop.media-handling automount false
```

---

### Post by Paddy Landau on 2012-05-02
Brilliant, thank you!

---

### Post by mc4man on 2012-05-02
More & more settings are being moved to gsettings so usually best place to look for first.

While it's getting quite populated a little exploring thru dconf-editor can prove useful to see what's available.

Also man gsettings lists some useful commands, ect.

---

### Post by nottestuser on 2012-05-20
Sorry to re-raise a solved problem but the listed setting does not work on my fresh install of 12.04:

```

$ sudo gsettings get org.gnome.desktop.media-handling automount 
false

```

Followed by a reboot yields the same automounting behavior as before. Are there multiple paths that result in automounting? Autofs is not installed. (Forgive me, I come from RHEL/Debian land where everything's in /etc.)

---

### Post by Paddy Landau on 2012-05-20
> **nottestuser said:**
> Sorry to re-raise a solved problem but the listed setting does not work on my fresh install of 12.04:
Why are you using sudo? Also, you don't need to reboot. A simple log out and log in again will do.

---

### Post by nottestuser on 2012-05-20
I'm using sudo because the idea of a per-user binary settings database is completely foreign to me. I'm slowly realizing now that Ubuntu =~ Windows, not Ubuntu =~ Unix.

Of course, for my user the automount setting is true. I've fixed that.

Thanks for the perspective adjustment.

Edit: And I need an xterm to run gsettings. This is a shift :)

---

### Post by Paddy Landau on 2012-05-21
> **nottestuser said:**
> ... the idea of a per-user binary settings database is completely foreign to me.
Linux was designed from the ground up to be a multi-user system. The idea is that no user, except root, can affect any other user. Whatever you do, a different user will be unaffected -- except when you run as root, i.e. sudo (for CLI) or gksudo (for GUI).

It is also possible for more than one user to be signed in and active at the same time on a Linux computer, although on a desktop that is quite rare.

> **nottestuser said:**
> ... I need an xterm to run gsettings.
On these forums we generally just call it a "terminal", "console" or "CLI" (command-line interface). The default terminal on Ubuntu is gnome-terminal, not xterm.

EDIT: You can run CLI commands from Alt-F2.

---

