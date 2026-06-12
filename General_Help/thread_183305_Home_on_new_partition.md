---
title: "Home on new partition"
date: 2006-05-27
forum: General Help
---

### Post by chloraldo on 2006-05-27
I want to transfer my home to a new partition. How can I do that? Anything important to consider?

---

### Post by Ramses de Norre on 2006-05-27
Check [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"), worked flawlessly for me.

---

### Post by chloraldo on 2006-05-27
[QUOTE=Ramses de Norre]Check [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"), worked flawlessly for me.[/QUOTE]
I can't umount my /home like it says on that page:
device is busy...

how can I force umount? other ideas?

I changed to / but it still says device is busy...

---

### Post by aysiu on 2006-05-27
You mean ```
sudo umount /mnt/newhome
``` doesn't work?

---

