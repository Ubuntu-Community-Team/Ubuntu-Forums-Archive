---
title: "is ubuntu need software like ccleaner (in windows) ?"
date: 2009-11-25
forum: General Help
---

### Post by plusnplus on 2009-11-25
Hi...,
Anyone know if ubuntu/ linux need something cleaning tools like ccleaner ([http://www.ccleaner.com](http://www.ccleaner.com))

---

### Post by *Linuxftw* on 2009-11-25
Check out BleachBit.
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by DeMus on 2009-11-25
> **plusnplus said:**
> Hi...,
Anyone know if ubuntu/ linux need something cleaning tools like ccleaner ([http://www.ccleaner.com](http://www.ccleaner.com))

The main structure in Linux is different from that in Windows.
Windows centralizes everything in one gigantic database called the registry. This is filled by everything and everyone, without being cleaned properly when, for instance, a program in uninstalled. This makes the registry become extremely large with .... nothing.
Now and then you need a program like ccleaner to clean-up.
It does more than cleaning the registry, it also cleans up after IE, FF and all other browsers. That part could be useful here as well to delete your browsing leftovers. On the other hand, in FF you can set the way you want to keep your history, typed-in info, etc. So, having a separate program to do that seems a bit overkill.

---

### Post by Andrew.Z on 2009-11-26
> **DeMus said:**
> This is filled by everything and everyone, without being cleaned properly when, for instance, a program in uninstalled. This makes the registry become extremely large with .... nothing.

On uninstallation Linux apps rarely/never clean up the files in the user home directories or the system directories like /var/logs and /var/cache.

> On the other hand, in FF you can set the way you want to keep your history, typed-in info, etc. So, having a separate program to do that seems a bit overkill.

BleachBit vacuums Firefox databases which become fragmented for space and speed, and Firefox does not offer an option for defragmentation.   Also BleachBit deletes old versions Firefox leaves behind on upgrades (such as you Firefox version 1 passwords) and optionally shred files to prevent file recovery.  Finally, BleachBit can clean ~70 applications at one time without the need to open each application individually.

---

### Post by bodhi.zazen on 2009-11-26
Much of the "cleaning" is performed automatically.

See : [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

