---
title: "Gnome Tweak Tool does not start."
date: 2012-06-08
forum: General Help
---

### Post by bhaveshnande on 2012-06-08
My gnome-tweak-tool does not start and this is what I get in terminal.
```
(gnome-tweak-tool:3681): GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.user-theme' is not installed

Trace/breakpoint trap (core dumped)

```
It does start when I give it root permissions, but still my Extensions list is empty.

Here's what I tried.
Reinstalling gnome-tweak-tool
Restarting Ubuntu 
Using: 
 sudo find ~ -user 0 -exec chown $USER:$USER {} +

-Ubuntu 12.04

---

### Post by bhaveshnande on 2012-06-09
Bump

---

### Post by Fuzzv on 2012-06-09
See this thread: [http://ubuntuforums.org/showthread.php?t=1950745]("http://ubuntuforums.org/showthread.php?t=1950745")

---

### Post by bhaveshnande on 2012-06-09
> **Fuzzv said:**
> See this thread: [http://ubuntuforums.org/showthread.php?t=1950745]("http://ubuntuforums.org/showthread.php?t=1950745")

Thank you. 
Someone should fix the User-theme-extension at extensions.gnome.org

---

