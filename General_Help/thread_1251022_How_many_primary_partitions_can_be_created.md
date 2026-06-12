---
title: "How many primary partitions can be created?"
date: 2009-08-27
forum: General Help
---

### Post by colau on 2009-08-27
Hi,
It's a 4GB pendrive.
Is it possible to create 2 primary partitions on that pendrive?

---

### Post by howefield on 2009-08-27
Yes

---

### Post by colau on 2009-08-27
> **howefield said:**
> Yes
I created two partitions using gparted.
I get these two partitions in ubuntu 9.04 but i can't get the second partition in windows.
Only the first partition is available in windows.
What may be the reason?

---

### Post by howefield on 2009-08-27
> **colau said:**
> What may be the reason?

Which file system have you formatted each partition with ?

---

### Post by P4man on 2009-08-27
the reason is windows. On removable storage, windows can only see the first partition. There is no way around this afaik.

Edit: Then again, what i do know :p here is a workaround/hack:

[http://www.ghacks.net/2008/10/16/how-to-create-multiple-usb-stick-partitions/](http://www.ghacks.net/2008/10/16/how-to-create-multiple-usb-stick-partitions/)

---

### Post by colau on 2009-08-27
> **howefield said:**
> Which file system have you formatted each partition with ?
fat32

---

### Post by P4man on 2009-08-27
doesnt matter what you filesystem you format them in, windows still wont see them, at least not without the hack I linked above (after edit).

---

