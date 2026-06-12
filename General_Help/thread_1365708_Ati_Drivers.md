---
title: "Ati Drivers?"
date: 2009-12-27
forum: General Help
---

### Post by Rdogg112 on 2009-12-27
Hey guys, is there a easy way to install the ati drivers , specifically the ATI Radeon 9250 ones??

Thanks In Advance!:)

---

### Post by vonn on 2010-03-23
Having the same problem with the same card on my parents computer. They got fed up with Windows so I told them I'd install Linux. Put Xubuntu and Ubuntu on there. Neither will run X with vertical sync, or correctly at all, for that matter. Stuck in a terminal only until someone can help...

---

### Post by 3rdalbum on 2010-03-23
EDIT: Sorry, I didn't realise that this was a thread bump.

Vonn, run this command:

```
sudo X -configure
```

It will create an xorg.conf file in your home directory (~/xorg.conf.new). Copy this to /etc/X11/xorg.conf:

```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```

Now edit the file:

```
sudo nano /etc/X11/xorg.conf
```

Where you see the part where it specifies the driver, change the driver from 'ati' to 'vesa'.

Save your changes and exit, by hitting Control-X, then Y, then Enter. Type:

```
sudo reboot
```

This should give you basic unaccelerated graphics.

---

### Post by vonn on 2010-03-23
Thanks for the help. Now back to trying a working driver with 3D-acceleration for a Radeon 2250 that works on Karmic... haha.

---

