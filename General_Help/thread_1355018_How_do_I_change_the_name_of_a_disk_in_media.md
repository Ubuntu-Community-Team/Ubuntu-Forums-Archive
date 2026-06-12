---
title: "How do I change the name of a disk in /media?"
date: 2009-12-14
forum: General Help
---

### Post by switch10 on 2009-12-14
When I upgraded to 9.10, Ubuntu renamed one of my external drives to a string of numbers.  Is there an easy way to change this name?

---

### Post by Dennis N on 2009-12-14
Give the mounted partition on the external drive a label. The drive will then mount at /media/label consistently.

See:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

and look at: Contents > Changing the Label

Note: 'Changing' also covers creating one.

---

### Post by howefield on 2009-12-15
You can also bring the drive up in Gparted and fill in the label field and apply.

---

### Post by vanadium on 2009-12-15
--deleted: my reply was erroneous--

---

### Post by switch10 on 2009-12-16
Thank you all!  I took care of it.

---

### Post by MaxIBoy on 2009-12-16
If your question has been solved, you can mark this thread as solved from the "thread tools" menu. That way anyone else googling for the same question can find the answers here and see that the thread contains a solution.

---

### Post by switch10 on 2009-12-16
> **MaxIBoy said:**
> If your question has been solved, you can mark this thread as solved from the "thread tools" menu. That way anyone else googling for the same question can find the answers here and see that the thread contains a solution.

Thanks

I was looking for that...

---

