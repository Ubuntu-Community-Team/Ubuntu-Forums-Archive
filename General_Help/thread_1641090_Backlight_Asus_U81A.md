---
title: "Backlight Asus U81A"
date: 2010-12-08
forum: General Help
---

### Post by dusanyu on 2010-12-08
I am experiencing the known bug for backlight on the Asus UL series laptops


untill this is resolved i found i can set the light to a decent level by running the command 

sudo setpci -s 00:02.0 F4.B=35


no is there a way i can set this to run invisibly at  at login ?

---

### Post by tredegar on 2010-12-08
> no is there a way i can set this to run invisibly at at login ?
Yes there is.
Here's an ugly hack, that will probably work, until something better comes up:

```
gksu gedit /etc/rc.local
```

Add the line **setpci -s 00:02.0 F4.B=35**
to the line before the final **exit 0** in that file.

No **sudo** is required, as that file is run as root.

Save.
Reboot.

---

### Post by dusanyu on 2010-12-08
Works splendidly as far as dirty hack it is still better than a dead battery.

---

