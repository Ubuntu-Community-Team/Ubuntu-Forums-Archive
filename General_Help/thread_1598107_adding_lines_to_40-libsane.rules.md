---
title: "adding lines to 40-libsane.rules"
date: 2010-10-16
forum: General Help
---

### Post by Ramot on 2010-10-16
Hi,
Finally I managed to install my printer/scanner drivers.
The last thing I need to do is to add the following two lines to 40-libsane.rules (which is a read only file):
  [LIST]
[*]# Brother scanners
[*]   ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
[/LIST]

How can I change permissions for this file or add these lines without changing permissions?

Thnx,
Sascha

---

### Post by halj32 on 2010-10-16
you can use a command promt (bash shell)
sudo gedit /(then where the file you want to open is)
enter password

edit file close & save
done

---

### Post by sisco311 on 2010-10-16
Hi and welcome to the forums!

You have to edit the file as root. Open a terminal and run:
```
gksu gedit /etc/udev/rules.d/40-libsane.rules
```

Edit the file then restart udev:
```
sudo udevadm control restart
```

You will probably have to reconnect the device for the new rules to take effect.

---

