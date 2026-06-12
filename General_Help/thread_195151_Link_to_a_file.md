---
title: "Link to a file"
date: 2006-06-12
forum: General Help
---

### Post by BrownieMan on 2006-06-12
Here's what I want to do... I want to create a file that basicaly when it is called or looked at or whatever it points to another file. So in essence I want to use this file as a channel for another file, a middle man basicaly.

Is there anyway to do this?

---

### Post by ayoli on 2006-06-12
ln -s /path/to/file /path/to/link

---

### Post by tonyr on 2006-06-12
[B]ln <existing-file-name> <new-file-name>
[/B]
creates a **hard** link:  existing file must be on same file system as new file name.

[B]ln -s <existing-file-name> <new-file-name>
[/B]
creates a **symbolic** link: existing file can be on another file system. See **man ln**.

---

### Post by gyterpena on 2006-06-16
Hi, I tryed sudo ln -s <existing-file-name> <new-file-name>  and I allways get: Operation not permitted
file I try to link is on win partion

Sorry, I figured it out.

---

### Post by aysiu on 2006-06-16
Middle-click-drag the file to where you want it and then select *link here*.

---

