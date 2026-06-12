---
title: "Exclude bad ram bytes"
date: 2012-06-16
forum: General Help
---

### Post by alenn on 2012-06-16
Hi all

I have 5 bytes (or bits, don't know) of bad Ram. How can I exclude these bytes so my Ubuntu 11.10 don't use them. My PC randomly freez, and when I ran memtest it reported 5 errors.

---

### Post by Cheesemill on 2012-06-16
I believe you can use the BADRAM parameter in GRUB to disable the section with errors.

However, I don't think that there is any reliable documentation on how to achieve this. Have a read of this thread and see if it's any help:
[http://ubuntuforums.org/showthread.php?t=1689890](http://ubuntuforums.org/showthread.php?t=1689890)

In my opinion the best thing to do is to replace the RAM that is giving you errors.

---

### Post by alenn on 2012-06-16
> **Cheesemill said:**
> I believe you can use the BADRAM parameter in GRUB to disable the section with errors.

However, I don't think that there is any reliable documentation on how to achieve this. Have a read of this thread and see if it's any help:
[http://ubuntuforums.org/showthread.php?t=1689890](http://ubuntuforums.org/showthread.php?t=1689890)

In my opinion the best thing to do is to replace the RAM that is giving you errors.

thank you, I excluded bad adresses in GRUB and I'll see if this works

---

