---
title: "GRUB: Error 21"
date: 2006-05-07
forum: General Help
---

### Post by danakatheone on 2006-05-07
OK, I installed Ubuntu on my second HD (windows is unaltered on the first) and grub asks me to configure and I let it configure for windows xp professional and ubuntu. I take out my second hard drive (the one with ubuntu on it). I assumed all the grub data was on the ubuntu hard drive, but it wasn't. When I try to boot into windows, it now says; "GRUB loading, please wait...." then the next line is "Error 21". How do i fix this?

---

### Post by JoshHendo on 2006-05-07
Ahh.

I had this problem too.

The problem is (i think) that it is on a slave HDD (is that right?). Split your windows one into 2 and install ubuntu on the second partition :).

---

### Post by danakatheone on 2006-05-07
I don't really want Ubuntu on the system anymore. I'd rather not have to reinstall windows either.

---

### Post by mcmillan on 2006-05-07
You'll need to reinstall the windows boot loader onto the master boot record. If you boot using the windows install cd there should be an option for recovery. I think the command from there is to type fixmbr, but I'm not certain about that.

---

### Post by az on 2006-05-07
[QUOTE=danakatheone] I assumed all the grub data was on the ubuntu hard drive,

. How do i fix this?[/QUOTE]

All the grub data is on the second hard drive.  However, The first stage of grub is still on the first hard dirve and it is looking for it's data (on the absent hard disk)

---

