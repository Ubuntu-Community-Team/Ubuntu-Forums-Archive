---
title: "permission denied when copy to usb"
date: 2011-01-03
forum: General Help
---

### Post by monoxide.tryst on 2011-01-03
Hi guys, Im running Ubuntu 10.10 on my hp mini 110 netbook, have been for since i upgraded from 10.04.  The problem Im having all of a sudden is when I try and copy anything from internal file system, to anything external [phone, card reader, usb hardrive] I get a pop up  that says Error opening file '/media/disk/<filename>': Permission denied  

Should be a quick fix i would think, what you guys got ???

---

### Post by hhh on 2011-01-03
For anything outside of your home directory you need root privileges, so open the run dialog (Alt+F2) and run "gksu nautilus" without the quotes. Be careful with files when you have root privileges!

---

### Post by monoxide.tryst on 2011-01-03
> **hhh said:**
> For anything outside of your home directory you need root privileges, so open the run dialog (Alt+F2) and run "gksu nautilus" without the quotes. Be careful with files when you have root privileges!


I guess i should have specified that I am moving thing from the home directory [music files and what not]

  But the problem also magically fixed itself : /

---

