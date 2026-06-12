---
title: "User permissions"
date: 2006-04-19
forum: General Help
---

### Post by Deactivator on 2006-04-19
When I mount ntfs disks from winXP, I can only use them as a root, not as user as I want.

I also can't log in the gaim msn as a user...

Any solutions?

---

### Post by pitkali on 2006-04-19
[QUOTE=Deactivator]When I mount ntfs disks from winXP, I can only use them as a root, not as user as I want.[/quote]
Edit your /etc/fstab file, for example enter in the terminal:
```
sudo gedit /etc/fstab
```
find the line with your ntfs disk and ensure it looks like this:
```
/dev/sda1       /windows        ntfs    defaults**,umask=0**        0       0
```
Notice the emphasised part - that's what will let you access files from non-root account.

---

