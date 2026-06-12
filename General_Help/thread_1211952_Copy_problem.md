---
title: "Copy problem"
date: 2009-07-13
forum: General Help
---

### Post by darthtony on 2009-07-13
Hi i cant copy a folder from desktop(amsnplus) to usr/share/amsn/plugins. with drag&drop, it say i cant, how can i do it from console?

---

### Post by Celauran on 2009-07-13
```
sudo cp /source /destination
```

---

### Post by CatKiller on 2009-07-13
You can run the file browser as [root]("https://wiki.ubuntu.com/RootSudo") with ```
gksudo nautilus
``` if you want to do it by drag-and-drop.

---

### Post by 3rdalbum on 2009-07-13
> **darthtony said:**
> Hi i cant copy a folder from desktop(amsnplus) to usr/share/amsn/plugins. with drag&drop, it say i cant, how can i do it from console?

None of the other posters explained the reason.

When you log into the desktop, you are logging in as a normal user, not as an administrator. This is really good - it means that you can't accidentally cause problems with the system, and any programs you run will be run as ordinary user as well so they are restricted in what they can do (i.e. buggy programs can't fill up your hard disk completely or cause other problems).

The location /usr/share/amsn/plugins is a restricted location - anyone can read from it, but only root ("administrator") can write to it. This is really good too, otherwise one user could steal another user's data by adding malicious plugins to aMSN, for instance. But most locations on your system are only writable by root, to protect users and the system.

When you run the command:

```
gksudo nautilus
```

It is saying "Run the 'nautilus' program as the root user". So a file browser window pops up with the same permissions as root, once you have been authenticated.

Only users who are allowed to become root, can perform commands using "gksudo" or its terminal equivilant, "sudo".

You can add an item to your right-click menu that quickly lets you open files and folders as root: Install the "nautilus-gksu" package from the Synaptic Package Manager, and the next time you log in you can right-click a file or folder and choose "Open as Administrator".

---

