---
title: "init 3?"
date: 2012-01-15
forum: General Help
---

### Post by shashanksingh on 2012-01-15
I need to kill xserver in order to install official Nvidia Graphic Drivers.

But whatever I have read doesnt seem to work.

```
sudo init 3
```

brings me back to pretty much the same place

```
sudo service gdm stop
``` and ```
sudo /etc/init.d/gdm stop
```

give me : Unknown instance

and if I just kill the xserver process, it just pops back again.
Its so persistent it just doesnt wanna go????:confused:

---

### Post by papibe on 2012-01-15
It looks like you are using 11.10. 'gdm' is no longer used. You should restart 'lightdm' instead:
```
sudo service lightdm stop
sudo service lightdm start
```
Hope it helps.
Regards

---

### Post by shashanksingh on 2012-01-15
Sure it helped. :)

---

