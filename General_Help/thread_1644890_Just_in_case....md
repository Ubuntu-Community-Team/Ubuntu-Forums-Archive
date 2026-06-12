---
title: "Just in case..."
date: 2010-12-13
forum: General Help
---

### Post by Don DeGregori on 2010-12-13
Scenario:
XP lover wants to try Unbuntu 10.10. I suggest download, burn  and try LiveCD. Now he wants install it as dual boot with XP. I help him with this chore. Somewhat later, he says he doesn't like Ubuntu and wants to remove it to and go back to XP like before.

I know there are a number of ways to do this, some complicated.I could read up on it again to help him out and send him the steps. 

So, could someone suggest an easy fool-proof way to do this "restore"? Don't want to ruin a friendship. A neat script running in the terminal would be super.

Thanks, Don

---

### Post by gordintoronto on 2010-12-13
If it's not a WUBI install, use gparted to remove the Ubuntu partition and then expand the size of the Windows partition.

---

### Post by oldos2er on 2010-12-13
FIRST, you'll want to restore Windows' boot loader, which I think you can do with the command fixmbr. Then reformat any Ubuntu partitions.

---

### Post by gordintoronto on 2010-12-14
Oops, my bad. Restoring the boot loader comes first.

---

### Post by Quackers on 2010-12-14
Usually with a Windows repair disc.

---

