---
title: "Disallow booting into another OS after hibernating"
date: 2010-05-02
forum: General Help
---

### Post by Exp HP on 2010-05-02
For a while, I've been using Hibernate so I can switch between Windows 7 and Ubuntu without having to close everything.  And today it just occurred to me that there are dangers associated with that.

Sure, the hibernation *state* is perfectly fine as long as you don't touch hiberfil.sys from Linux or the swap partition from Windows.  But that's not the issue.

I auto-mount the c: drive in Ubuntu.  I often work on the same file in both OSes simultaneously.  I might even rename a folder that's currently the working directory for a program in the other OS. I dunno, I guess I'm an idiot like that.


I need to keep myself from booting into one OS while the other is hibernating.   Otherwise, one of these days I'm going to break this poor computer.
Perhaps I get GRUB to recognize when I've hibernated in an OS (and disallow the other OS accordingly)?  Or use another bootloader that does protect against doing this?

---

### Post by Exp HP on 2010-05-08
Bump

---

