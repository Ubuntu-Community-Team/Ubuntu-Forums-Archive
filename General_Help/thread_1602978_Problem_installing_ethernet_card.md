---
title: "Problem installing ethernet card"
date: 2010-10-22
forum: General Help
---

### Post by nHacker on 2010-10-22
I recently installed an Intex PCI Ethernet Card (model no. IT-584) on my PC. It works perfectly in Windows even without installing the given drivers. But it doesn't seem to work in Ubuntu. The network icon displays 'disconnected'. I tried to install the driver from the given CD, there I found a rtl8139.c file and tried to compile it, but couldn't. I also downloaded a compiled .o file ([http://www.szabilinux.hu/rtl8139/rtl8139.o](http://www.szabilinux.hu/rtl8139/rtl8139.o)) and tried to install it, but there were errors:
```

sudo insmod rtl8139.o
insmod: error inserting  'rtl8139.o': -1 Invalid module format

```
Now I don't know what to do. Please help.

---

### Post by P4man on 2010-10-22
Long shot, but see here:
[http://ubuntuforums.org/showthread.php?t=1516006](http://ubuntuforums.org/showthread.php?t=1516006)

If that isnt your problem,  can you report the output of 
```
lspci
```
and 
```
lshw -C network
```

---

### Post by nHacker on 2010-10-22
Thanks P4man. That was exactly my problem. (I used to hibernate WinXp often.)
Thanks again! :-)

---

### Post by P4man on 2010-10-22
Glad it helped. Im still curious as to why ubuntu cant enable or wake up the NIC though. Id consider that a bug.

---

