---
title: "Firefox won't load"
date: 2010-02-17
forum: General Help
---

### Post by JohnnyArch on 2010-02-17
Hi all,
I'm an Ubuntu beginner (running 9.10). Somehow Firefox starts to load then quits. However, I discovered that I can run it as root in the terminal with the following message:
root@john-desktop:/home/john# firefox

(firefox:4415): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4415): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4415): GLib-WARNING **: g_set_prgname() called multiple times

I've uninstalled the package and reinstalled to no avail. Suggestions? Thanks.

---

### Post by lovinglinux on 2010-02-17
Start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and test it. If it works, then you probably have a corrupt file on your profile, sub-optimal settings or an extension preventing FF form starting.

To find if it's an add-on, close Firefox and start your default profile with this command:

```
firefox -safe-mode
```

If that works, then you need to find which add-on is causing the problem.

---

