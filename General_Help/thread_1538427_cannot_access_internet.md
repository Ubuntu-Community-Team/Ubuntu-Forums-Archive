---
title: "cannot access internet"
date: 2010-07-25
forum: General Help
---

### Post by ankit.vader on 2010-07-25
i've just installed Lubuntu 10, but i cannot access internet from it. I've to access internet from a mobile through data cable, but whenever I connect data cable nothing shows up in Network Manager. Can some one help?

PS:: I can access internet using mobile in ubuntu 10.

---

### Post by dineshs on 2010-07-25
Did you try this?
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab Mobile broadband -add-proceed

---

### Post by ankit.vader on 2010-07-25
yes i tried that, i added the connection successfully, but it still does not show up in network manager.

---

### Post by dineshs on 2010-07-25
Did you tick [COLOR="Blue"]Available to all users[/COLOR] while configuring?

---

### Post by ankit.vader on 2010-07-25
yes..

---

### Post by ankit.vader on 2010-07-25
yes..
in the network manager nothing shows up, except for VPN.

---

### Post by dineshs on 2010-07-25
Pl post the output of ```
lsusb
```and
```
dmesg | grep -e "modem" -e "tty"
```

---

### Post by ankit.vader on 2010-07-25
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 010: ID 0421:006b Nokia Mobile Phones 
Bus 002 Device 009: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by dineshs on 2010-07-25
Is there any provision for setting your mobile in PC suite mode?What model is it

---

### Post by ankit.vader on 2010-07-25
```
[    0.000000] console [tty0] enabled
[    0.323691] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.324240] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.343939] cdc_acm 3-2:1.0: ttyACM0: USB ACM device
[    6.346903] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 2982.147616] cdc_acm 2-2:1.1: ttyACM0: USB ACM device

```

yes there is a provision for pc suite.

---

### Post by dineshs on 2010-07-25
And did you select that option in the mobile.I think you should

---

### Post by ankit.vader on 2010-07-25
yes i selected pc suite.

---

### Post by dineshs on 2010-07-25
can you try this command
```
sudo modprobe usbserial vendor=0x0421 product=0x006b
```
restart

---

### Post by ankit.vader on 2010-07-25
i tried that, still nothing happens.

---

