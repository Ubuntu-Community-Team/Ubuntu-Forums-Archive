---
title: "Install on a Netbook"
date: 2011-07-23
forum: General Help
---

### Post by Phil Binner on 2011-07-23
I'm having problems installing Ubuntu on my netbook. I tried the Wabi, but it asks for a password. The windows system does not have a password. If I put my password in I get a message "passwords don't match". Only one password field is available. If I leave the password out to make it match windows it asks me for a valid password.

Actually, I don't want to run Ubuntu iside windows, I want it by itself, so Wabi is not really what I want. Can anybody point me to a tutorial as to how to do a clean install on a netbook.

Thanks, Phil B

---

### Post by Matt__ on 2011-07-23
Try this one
[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)
(assuming you will try 11.04)

---

### Post by Mark Phelps on 2011-07-23
> **Phil Binner said:**
> Actually, I don't want to run Ubuntu iside windows, I want it by itself ... 

Wubi doesn't actually run Ubuntu inside MS Windows; it installs it inside an MS Windows partition.  But, in general, it's better to have it in its own partitions.

Just do NOT use the Ubuntu installer or GParted to shrink the Win7 OS partition to make room for Ubuntu (if you want to do a dual-boot setup).  Use the Win7 Disk Management tool to shrink Win7 OS partition.

---

### Post by Phil Binner on 2011-07-28
I did have some trouble following that instruction on the netbook. The startup stick did get created - it had to be re-formatted as a pendrive - but when I tried to boot from it it didn't get past the first line. Fortunately I was able to put the pendrive and a startup CD into an Ubuntu machine, and created a startup disk through the menus. All well now.

---

