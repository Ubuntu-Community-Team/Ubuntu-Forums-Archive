---
title: "Disable user list in GDM?"
date: 2011-12-26
forum: General Help
---

### Post by josephellengar on 2011-12-26
I'm using GDM on a newly installed 11.10. I am trying to do two things with it:

1) Disable the user list
2) Disable the "drum roll" system ready sound

I know which gconf keys I have to modify for this to work, but obviously I can't do this with sudo or a regular user, because GDM won't read those users, so I have to do it with sudo -u gdm.

In the past (releases  I have been able to go into tty1, log in as myself, and then do:

```

export DISPLAY=:0.0
sudo -u gdm gconf-editor

```

Then I could modify the keys, uncheck "play sound" and "show user list" or whatever the keys were called. I could also do a ```
sudo -u gdm gnome-control-center
```
to change the background and theme of gdm.

Now, when I try to call one of these programs that way (or from within a normal gnome session) I get a number of errors about Dbus problems, parsing, etc. I can't give you the exact text because it wouldn't save. I tried piping it, redirecting it, and even using the `script` command, but none of those worked to save it.

Anyway, do you have any idea why this might be happening?

---

### Post by josephellengar on 2011-12-27
bump

---

