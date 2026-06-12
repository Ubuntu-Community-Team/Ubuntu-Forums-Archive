---
title: "edit the rcS file"
date: 2012-04-29
forum: General Help
---

### Post by athalsten on 2012-04-29
recently i install the ubuntu 12 . Its good. But the time is in UTC . I want change it . But the etc/defult/rcS cannot be edited. It says u are not the user.u cannot edit this file.plz anyone help me how can i change the UTC=no.

---

### Post by oldos2er on 2012-04-29
First make a backup copy ```
sudo cp /etc/default/rcS /etc/default/rcS.backup
``` then open the file in gedit with root (admin) privileges ```
gksu gedit /etc/default/rcS
```

---

### Post by athalsten on 2012-04-29
> **oldos2er said:**
> First make a backup copy ```
sudo cp /etc/default/rcS /etc/default/rcS.backup
``` then open the file in gedit with root (admin) privileges ```
gksu gedit /etc/default/rcS
```

thanks for answer.but  I am new in ubuntu.i just setup it today and update it.the user is set as adminstrator. But when i right click it, it says ur not an admin.so u cant edit it. What i do to get as an admin

---

### Post by imachavel on 2012-04-29
sudo -i

but to edit things in the gui:

gksu edit - then a gui window will appear, and you will have full gui privileges

---

### Post by athalsten on 2012-04-29
> **imachavel said:**
> sudo -i

but to edit things in the gui:

gksu edit - then a gui window will appear, and you will have full gui privileges


thanks friend,u helped me very much.searching this thing from last few weeks.now i have no electrysity when electrycity is back ill try it.thanks again

---

### Post by matt_symes on 2012-04-29
Hi

Why not just use hwclock ?

```
sudo hwclock --localtime
```

Kind regards

---

### Post by athalsten on 2012-05-01
> **imachavel said:**
> sudo -i

but to edit things in the gui:

gksu edit - then a gui window will appear, and you will have full gui privileges

thanks it work.just it was sudo-i and gksu gedit- work perfect. Thanks again

---

