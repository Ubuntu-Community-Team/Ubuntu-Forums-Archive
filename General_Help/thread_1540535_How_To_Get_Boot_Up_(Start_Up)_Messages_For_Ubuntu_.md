---
title: "How To Get Boot Up (Start Up) Messages For Ubuntu 10"
date: 2010-07-27
forum: General Help
---

### Post by cadaverousmob on 2010-07-27
I would like to get system information and status messages upon startup. This old thread doesn't work since menu.lst ceases to exist on subsequent versions after Dapper: [http://ubuntuforums.org/showthread.php?t=286971](http://ubuntuforums.org/showthread.php?t=286971)

Can someone please tell me how to enable messages to display on screen upon startup for Ubuntu 10? Thanks!

---

### Post by LegendofTom on 2010-07-28
Now that Ubuntu uses grub2, you will need to edit /etc/default/grub.
 
Change:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

then update your grub config with
```
sudo update-grub
```

Legend

---

### Post by cadaverousmob on 2010-07-28
Thanks, Tom!

---

### Post by LegendofTom on 2010-07-28
No problem.

Tom

---

### Post by LegendofTom on 2010-07-28
Double Post

---

