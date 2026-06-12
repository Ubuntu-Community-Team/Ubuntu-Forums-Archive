---
title: "best system for syncing files to back up from a windows machine?"
date: 2009-12-25
forum: General Help
---

### Post by violetdream on 2009-12-25
I bought a new desktop and installed Ubuntu on it as well as pulling my 1tb backup hard drive and mounting it in the case. I got it to mount (it's NTFS) but I was wondering what is the best way to interface between the two computers - I imagine there's a way to do it with a usb cable, lan, or firewire, but what would be the easiest? I don't have an extra cable atm, but if I were just to plug a USB cable between the two, it would be awesome if it just showed up as an external drive on my windows machine. Also, is it dangerous to have my ntfs volume in linux? I'm not sure how stable the support for this file system is on linux (seems to mount ok, in any case).

Sorry for the silly question - it's just that I'll be buying cables tomorrow and wanted to know if I should get a certain type to facilitate transfer. Thanks!

---

### Post by x33a on 2009-12-25
you'll need to install samba for sharing b/w the 2 computers. get a lan wire and setup samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

in case you want to keep them synced, you can try rsync.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by audiomick on 2009-12-25
Between 2 computers without a switch or a router you theoretically need a crossover ethernet cable. It is a bit less relevant these days, as most ethernet ports these days are "smart" enough to sort it out, but it is not a bad idea to have the right cable anyway.

---

