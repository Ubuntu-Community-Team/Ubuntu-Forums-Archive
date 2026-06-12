---
title: "Ethernet is not Activated at Boot Time"
date: 2010-09-24
forum: General Help
---

### Post by Penguin Guy on 2010-09-24
When my computer first starts I cannot access any ethernet devices (i.e. [FONT="Courier New"]ifconfig[/FONT] returns only [FONT="Courier New"]lo[/FONT]) until I run [FONT="Courier New"]dhclient[/FONT] or [FONT="Courier New"]dhclient3[/FONT].

Here's my [FONT="Courier New"]/var/log/boot.log[/FONT]:
```

[COLOR="Gray"]fsck from util-linux-ng 2.17.2
Ubuntu_10.04: clean, 307104/655360 files, 2042504/2620587 blocks[/COLOR]
init: portmap main process (829) terminated with status 2

init: portmap main process ended, respawning

init: statd pre-start process (844) terminated with status 2

 * Starting AppArmor profiles       [160G modem-manager: Loaded plugin MotoC

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

```

Anyone know what could be causing this?

---

### Post by andrewthomas on 2010-09-24
Did you uninstall NetworkManager?

---

### Post by Penguin Guy on 2010-09-24
> **andrewthomas said:**
> Did you uninstall NetworkManager?
No, network-manager is installed and up-to-date.

---

### Post by andrewthomas on 2010-09-24
post the output of 

```
cat /var/log/syslog|grep dhclient
```

---

### Post by efflandt on 2010-09-24
In **Network Connections** is your Auto eth, or whatever it is, checked to **Connect automatically** and **Available to all users**?  If the latter is NOT checked, maybe it only connects when a specific user allowed to connect it is logged in, instead of right away for any user(s).

Does it automatically connect when "you" log into X?

---

### Post by Penguin Guy on 2010-09-26
Looks like it's fixed itself. Odd.

---

