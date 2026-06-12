---
title: "where to find ssh-mounted directories"
date: 2010-12-26
forum: General Help
---

### Post by jmvidalvia on 2010-12-26
Hi!
I go to places-acces server-ssh and connect to a remote server with Nautilus.
All ok.
But I prefer to use vifm as my main file manager: I try to find the ssh-mounted devices in /mnt or /media but cannot fin them.
Does anybody know where they are?
Thanks!

---

### Post by prshah on 2010-12-26
> **jmvidalvia said:**
> I try to find the ssh-mounted devices in /mnt or /media but cannot fin them.

Locations mounted via Places->Connect to server are browseable in ~/.gvfs (~ indicates your home directory)

---

### Post by jmvidalvia on 2010-12-26
Great! thanks.
BTW, is the system using sshfs to mount those units?

> **prshah said:**
> Locations mounted via Places->Connect to server are browseable in ~/.gvfs (~ indicates your home directory)

---

