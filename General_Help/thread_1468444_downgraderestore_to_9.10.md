---
title: "downgrade/restore to 9.10?"
date: 2010-05-01
forum: General Help
---

### Post by mshenrick on 2010-05-01
after installing 10.04 loads of problems have arised accumulating to no GUI.

i doubt this is possible unlike windows.

i havent made any backups but could i restore it to 9.10 or copy my home dir to an external drive in text only (cant use live cd, its encrypted) and reinstall? (commands on that would help!)

---

### Post by Mark Phelps on 2010-05-01
> **mshenrick said:**
> after installing 10.04 loads of problems have arised accumulating to no GUI.

i doubt this is possible unlike windows.

i havent made any backups but could i restore it to 9.10 or copy my home dir to an external drive in text only (cant use live cd, its encrypted) and reinstall? (commands on that would help!)

You can try the copy /home, reinstall 9.10, re-copy /home -- and it might work, but there are no guarantees.

---

### Post by Martiini on 2010-07-04
to downgrade a Debian distro, one must use apt-pinning .... which means .. you create 
etc/apt/preferences  file ...

Package: *
Pin: release a=karmic
Pin-Priority: 1001

Package: *
Pin: release a=karmic
Pin-Priority: 60

Package: *
Pin: release a=lucid
Pin-Priority: 50


[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)
gives the full story and describes subject in depth ...

in case you get pkg errors .. you use .. dpkg -i --force-all / dpkg -r --force-all

---

