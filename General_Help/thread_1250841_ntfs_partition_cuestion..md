---
title: "ntfs partition cuestion."
date: 2009-08-27
forum: General Help
---

### Post by armagedonc on 2009-08-27
Hello everyone, well my ubuntu haunty is running good. only a doubt.
Why can I play my files from ntfs partition even when I'm not the owner?  :)

---

### Post by beastrace91 on 2009-08-27
I'm assuming your ntfs partition is your Windows install? If so this is because Windows does not use the same file permissions as Nix

~Jeff

---

### Post by armagedonc on 2009-08-27
> **beastrace91 said:**
> I'm assuming your ntfs partition is your Windows install? If so this is because Windows does not use the same file permissions as Nix

~Jeff

yeah is dual boot, that means that the owner in a ntfs partition doesent really matters.?

---

### Post by beastrace91 on 2009-08-27
Well if your write files to the ntfs partition from Ubuntu then it will have the respective owner ship properties (on Linux). But Windows does not honor Linux permissions and vice versa.

~Jeff

---

### Post by armagedonc on 2009-08-28
> **beastrace91 said:**
> Well if your write files to the ntfs partition from Ubuntu then it will have the respective owner ship properties (on Linux). But Windows does not honor Linux permissions and vice versa.

~Jeff

well,but my music folder is owned by the root account, but I still can play music files from it, of course with a non root account. thats a contradiction.

---

### Post by P4man on 2009-08-28
its not a contradiction. root may own it, but see who has folder access. You may well have read/write permission on it even though you dont own it.

---

### Post by Copernicus1234 on 2009-08-28
Yes, learn about Linux file permissions. Usually the default is that anyone can read a file but only the owner can modify it.

---

### Post by vanadium on 2009-08-28
Owner of an ntfs volume is root, and permissions are by default all open (read, write, execute) for owner, group and others.

You can restrict permissions of the entire volume by changing the permissions of the mount point of the drive.

When mounting the drive using /etc/fstab, you can control ownerschip and permissions from there using ntfs specific options.

---

