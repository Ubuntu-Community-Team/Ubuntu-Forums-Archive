---
title: "is remote desktop from ubuntu to windows possible?"
date: 2010-04-20
forum: General Help
---

### Post by plusnplus on 2010-04-20
Hi all,

is remote desktop from windows to ubuntu possible?

so far i googling, only found from ubuntu to windows.

Thanks for any relpy/ help

---

### Post by foxmulder881 on 2010-04-20
Of course. I do it everyday to manage my headless windows based server. Just use Gnome-RDP.

```
sudo apt-get install gnome-rdp
```

---

### Post by new_tolinux on 2010-04-20
In 9.04 there was by default a tool in Applications - Internet, called Remote Desktop that worked for me. Not to be confused with Tools - Preferences - Remote Desktop (which shares your Ubuntu desktop through VNC).

Can't see it's exact location/name/properties: the harddisk of my ubuntu-laptop is waiting for replacement due to bad sectors.

---

### Post by 405jayb on 2010-04-20
I use rdesktop. From terminal type: rdesktop -u username hostip. Exampe: rdesktop -u james 192.168.2.8

---

### Post by plusnplus on 2010-04-20
Hi all,
really sorry, what i mean is from windows to ubuntu.

---

### Post by new_tolinux on 2010-04-20
> **plusnplus said:**
> Hi all,
really sorry, what i mean is from windows to ubuntu.
:lolflag:

Try [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by plusnplus on 2010-04-20
Hi new_tolinux,
Thanks, i can connect/ remote desktop to ubuntu from window now.

---

