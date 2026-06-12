---
title: "Slow Wireless Connection in Ubuntu"
date: 2011-03-29
forum: General Help
---

### Post by dAii7 on 2011-03-29
I just switched to Ubuntu from Windows 7 Ultimate 64Bit, and before I switched all of my drivers are up to date and now that did a dual boot with Ubuntu 10.10 my internet seems to be very slow and it was fast how it should be with Windows 7. I have Cable.

Also, if anyone has any news if Adobe releasing Adobe CS5 to Linux users, because it's not the same having it with Wine or any other way and I dont want to use GIMP neither. :KS

---

### Post by TBABill on 2011-03-29
It's possible your driver is not configured properly in Ubuntu. You'll need to provide more info before we can know for sure. However, Ubuntu does NOT use your Windows drivers so updating them has no effect on Ubuntu whatsoever. They are separate operating systems using their own drivers.
 
Can you open a terminal and enter the following codes, then paste back here what the results of those inputs are?
 
```
lspci
```
 
```
sudo lshw -C network
```
 
Then open these two files and copy/paste the contents:
 
/etc/modules
/etc/modprobe.d/blacklist.conf

---

