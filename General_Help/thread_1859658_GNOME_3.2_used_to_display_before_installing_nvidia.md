---
title: "GNOME 3.2 used to display before installing nvidia drivers"
date: 2011-10-14
forum: General Help
---

### Post by GideonB on 2011-10-14
I installed some NVIDIA drivers (the recommended ones from jockey) and now I cannot use GNOME 3.2
The graphics card I'm using on this PC is a NVIDIA 6600 (not sure if its GT or GTX, it's old though xD)

Thanks for any help provided

---

### Post by TeoBigusGeekus on 2011-10-14
Boot up from recovery mode and, once in terminal, give
```
rm /etc/X11/xorg.conf
```
to delete your xorg file. Then
```
reboot
```
to reboot (surprise) and try to install an older version of the NVidia drivers.

---

### Post by GideonB on 2011-10-14
Thanks for the help
I managed to get the drivers to work again after re-enabling the driver myself but thanks for the help anyways

---

