---
title: "Where are my bash profiles and gnome panels stored?"
date: 2010-01-05
forum: General Help
---

### Post by drwhofan on 2010-01-05
I have a bash profile (with custom terminal color settings) and also a gnome panel (with quick-launchers on it and other customizations). Assuming these things are stored in text files, where in my ~home directory can I find them? I ask because I want to duplicate them on a another linux box to have the same bash profile/taskbar, and If I can do it by copying files instead of manually recreating them, it would be better.

---

### Post by drs305 on 2010-01-05
The gnome-terminal settings are stored in /home/drs64/.gconf/apps/gnome-terminal/profiles/

You can save the panel settings with this command:
```
gconftool-2 --dump /apps/panel > */path/filename*
```

Restore them with:
```
gconftool-2 --load < */path/filename*
```

However, restoring them to another computer can be problematic, since they can reference objects with numbers that won't necessary match in the new machine.

---

### Post by howefield on 2010-01-05
> **drwhofan said:**
> Assuming these things are stored in text files, where in my ~home directory can I find them?

Don't know about your scripts but the panel info would be here

```
~/.gconf/apps/panel
```

---

