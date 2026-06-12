---
title: "Mounting points on desktop"
date: 2004-10-24
forum: General Help
---

### Post by Dracontopes on 2004-10-24
I recently mounted my windows ntfs partitons in etc/inittab

Now, all the drives appear on the desktop... I don't want them there, is there a way to remove them from desktop? Moving to Wastebasket is greyed out...

---

### Post by FLeiXiuS on 2004-10-24
First off, you should mount them to /etc/fstab


Then I belive you can browse around here..

Applications > System Tools > Configuration Editor, navigate to /apps/nautilus/general or desktop, i forgot...currently not booted into ubuntu so try it your self.  It should be a checkbox option.

---

### Post by Dracontopes on 2004-10-24
Thanks!

Gconf editor -> apps -> nautilus -> desktop -> volumes visible checkbox! :D

---

