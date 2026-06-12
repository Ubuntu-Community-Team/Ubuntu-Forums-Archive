---
title: "how to pass nosplash to kernel"
date: 2009-11-25
forum: General Help
---

### Post by frederikbjerreandersen on 2009-11-25
Hi,

I just bought a Lenovo s12. In the ubuntu-wiki, it's said to run pretty well...and it does. Only the startup is a little long (and not at alle near the 30 secs). The wiki recommends "passing "nosplash" to kernel do avoid long delay at bootup with Karmic"

ok...but how do you exactly do that?

f

---

### Post by sisco311 on 2009-11-25
Backup the /etc/default/grub file:
```
sudo cp /etc/default/grub /etc/default/grub-backup
```

Edit it:
```
gksu gedit /etc/default/grub
```

replace:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
with
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash"
```
or 
```
GRUB_CMDLINE_LINUX_DEFAULT="nosplash"
```
save the file and exit.

run:
```
sudo update-grub
```

[uhelp]community/Grub2[/uhelp]

---

