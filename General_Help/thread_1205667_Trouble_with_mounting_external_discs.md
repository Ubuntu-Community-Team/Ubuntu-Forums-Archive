---
title: "Trouble with mounting external discs"
date: 2009-07-06
forum: General Help
---

### Post by tulpaner on 2009-07-06
I am not able to mount external discs through the USB-port. When I run "sudo fdisk -l" with the discs connected and switched on I can't find them at all. This is the outcome from "sudo fdisk -l":

[I]Disk /dev/sda: 100,0 GB, 100030242816 byte
255 huvuden, 63 sektorer/spår, 12161 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x868b868b

Enhet    Start   Början      Slut     Block    Id  System
/dev/sda1   *         1     11787    94679046   83  Linux
/dev/sda2         11788     12161     3004155    5  Utökad
/dev/sda5         11788     12161     3004123+  82  Linux växling / Solaris[/I]

I am running Ubuntu 9.04. I have two FAT32 discs. My cellphone (Nokia E73) doesn't show up anywhere either.

---

### Post by taurus on 2009-07-06
What about

```
dmesg | tail
```

---

### Post by tulpaner on 2009-07-06
This is the outcome from "dmesg | tail":

[   26.857915] [drm] writeback test succeeded in 1 usecs
[   30.051136] r8169: eth0: link down
[   30.051383] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.424163] eth1: no IPv6 routers present
[   67.053656] CPU0 attaching NULL sched-domain.
[   67.053736] CPU0 attaching NULL sched-domain.
[   67.131924] CPU0 attaching NULL sched-domain.
[   67.132251] CPU0 attaching NULL sched-domain.
[   69.675496] ieee80211_crypt: registered algorithm 'TKIP'
[  953.656038] ACPI: EC: missing confirmations, switch off interrupt mode.

---

### Post by taurus on 2009-07-06
First, make sure you turn on the power of the drive first before you plug it in.

Second, try another USB port.

Third, try another USB cable if you have an extra cable laying around.

Or try to connect that external drive to another machine and see if it works.

---

### Post by tulpaner on 2009-07-07
I have done all that. There seems to be no connection through none of the three USB-ports I have on the computer. I also tried to connect my USB-mouse, but nothing happens there either. All the external drives works fine on my Windows-based computer. I have also reinstalled Ubuntu 9.04 a few times but the problem still maintains.

---

### Post by tulpaner on 2009-07-15
Any new ideas?

---

