---
title: "Permanent Text Based"
date: 2009-09-07
forum: General Help
---

### Post by Monotoko on 2009-09-07
Hiya ^.^

Im running Ubuntu linux inside a VM because it is better for programming on, and most of the perl/python modules i use are linux-only.

All of these programs are purely text based...so i was wondering if it would be possible to make the VM boot into text-mode, cos i usually end up just pressing ctrl+alt+f1 anyways...and i cant see the point in having a GUI up that i do not use...

Anyone know?

Cheers
~Monotoko

---

### Post by Monotoko on 2009-09-07
My appologies...never saw the post under mine..issue resolved ^.^

---

### Post by ddrichardson on 2009-09-07
```
sudo update-rc.d -f gdm remove
```

---

### Post by Monotoko on 2009-09-07
Yepp...and for anyone else who searches...

To undo the changes:

```
sudo update-rc.d gdm defaults 30 01
```

---

### Post by ddrichardson on 2009-09-07
Actually, to tow the party line, I should also mention System->Administration->Service and enabling or disabling GDM.

---

