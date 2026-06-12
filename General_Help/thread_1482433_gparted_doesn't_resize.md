---
title: "gparted doesn't resize"
date: 2010-05-13
forum: General Help
---

### Post by david sousa on 2010-05-13
Hey!

Im using the lastest buntu in tohsiba nb100 and now i want to make a new partition for windows. wich means i have to resize the only one i have. To do this im using gparted in a "liveusb" ubuntu.

However, option resize/move (or something like that) does not apear clickable. But the hard disk is unmounted...

How do i solve this? any clues?...

thanks 

David Sousa

---

### Post by mike555 on 2010-05-13
perhaps your live Ubuntu is using your swap file? try swapoff command

---

### Post by david sousa on 2010-05-13
i love you

---

### Post by zarap on 2010-05-13
You could try to start gparted from terminal with root privileges.
gksudo gparted
That worked for me

---

