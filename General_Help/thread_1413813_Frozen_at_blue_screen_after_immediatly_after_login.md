---
title: "Frozen at blue screen after immediatly after login"
date: 2010-02-22
forum: General Help
---

### Post by williamo123 on 2010-02-22
Hi, I would appreciate any help because I cannot access my system. While I was trying to install a package in the package manager I accidentally removed a package that I am not aware of. I got a crash report telling me to enter something along the lines of a broken package repair mode. The next time I started my computer it froze at the blue screen with bubbles after login. Is there a way to access the gui using a recovery/rescue type mode so I can access the package manager, or is there a way to find and reinstall the vital package?

---

### Post by Zorael on 2010-02-23
Difficult to say. You may even be able to just hit Alt+F2 when you're at said blue bubbly screen, and start the applications you like. You'll want to open up a terminal, and you want a working net connection.

If Alt+F2 works, what has happened is probably that something critical to the plasma desktop environment isn't installed (or failed to configure). Everything is probably running in the background, you just don't see it since you don't have a task manager or a system tray. That means the networking manager should still be running, and hopefully automatically connected you to your network (and set up your internet connection).

If you're on a wired connection with automatic IP assignment (DHCP), you can probably just boot up in recovery mode and pick **network root** (or something along those lines).

Once net connection is established;
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```

Then reboot, or log out and back in.

---

