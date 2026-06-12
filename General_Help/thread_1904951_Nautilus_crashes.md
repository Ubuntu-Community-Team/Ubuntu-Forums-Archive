---
title: "Nautilus crashes"
date: 2012-01-05
forum: General Help
---

### Post by sbsin on 2012-01-05
Can't open folders using nautilus, although the desktop seems to be working. I know my way around the terminal but don't know how to debug nautilus, launching nautilus from terminal won't give me any information.

Ubuntu 10.04

Update:
- I've tried uninstalling ubuntu-one & dropbox.
- Works when I run gksudo nautilus
- nautilus --no-desktop --browser, still crashes

---

### Post by TeoBigusGeekus on 2012-01-06
Try running bleachbit as a normal user to see if deleting cache, thumbnails, etc. solves the issue.

---

### Post by x C0MMAND0 x on 2012-01-06
+1 Bleachbit.

As an alternate test, can you run a different file browser such as Dolphin to see if that can browse okay?

---

### Post by sbsin on 2012-01-06
> **TeoBigusGeekus said:**
> Try running bleachbit as a normal user to see if deleting cache, thumbnails, etc. solves the issue.

Thanks, I tried bleachbit but it didn't help.

[QUOTE=x C0MMAND0 x]
+1 Bleachbit.

As an alternate test, can you run a different file browser such as Dolphin to see if that can browse okay?[/QUOTE]

Thunar works, nautilus works for other users

--

More information:
- I can currently view all files outside of /home/specific_user using nautilus. When I open /home/specific_user folder it crashes immediately.

---

