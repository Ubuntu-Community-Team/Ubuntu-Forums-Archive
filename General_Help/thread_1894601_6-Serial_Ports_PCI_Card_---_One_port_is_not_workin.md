---
title: "6-Serial Ports PCI Card --- One port is not working"
date: 2011-12-12
forum: General Help
---

### Post by huntkey on 2011-12-12
Hi experts,
 
I recently bought this card on Ebay to give me 6 serial ports for managing my  Cisco routers and switches for my home lab. 5 of them work fine except  1... I suspect that it is a broken port. However how can I verify it? I'm really not expert of Linux anyway. The serial console  simulator software I use is minicom.

The symptom is that there is no response. When connected the minicom  shows that it is "Offline". The same console cable and device works on  another serial port so the device and the cable should be good.

 ```
dzhao@Ubuntu:~$ setserial -g /dev/ttyS* | grep -v unknown
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS4, UART: 16650V2, Port: 0xe080, IRQ: 16
/dev/ttyS5, UART: 16650V2, Port: 0xe400, IRQ: 17
/dev/ttyS6, UART: 16550A, Port: 0xec00, IRQ: 18
/dev/ttyS7, UART: 16550A, Port: 0xe880, IRQ: 18
/dev/ttyS8, UART: 16550A, Port: 0xe800, IRQ: 18
/dev/ttyS9, UART: 16550A, Port: 0xe480, IRQ: 18
``` ```
+-----------------------------------------------------------------------+
| A -    Serial Device      : /dev/ttyS8                                |
| B - Lockfile Location     : /var/lock                                 |
| C -   Callin Program      :                                           |
| D -  Callout Program      :                                           |
| E -    Bps/Par/Bits       : 9600 8N1                                  |
| F - Hardware Flow Control : No                                        |
| G - Software Flow Control : No                                        |
|                                                                       |
|    Change which setting?                                              |
+-----------------------------------------------------------------------+
```

All other serial ports have the same config. Is there anything else other than hardware problem which could cause this?

Thanks!

---

### Post by oldtimer7777 on 2011-12-13
Perhaps the issue is located in your .minirc.dfl file. I just have hunch about it since it is automatically created. You may need to also manually configure something like that to get it to work. 

> **huntkey said:**
> Hi experts,
 
I recently bought this card on Ebay to give me 6 serial ports for managing my  Cisco routers and switches for my home lab. 5 of them work fine except  1... I suspect that it is a broken port. However how can I verify it? I'm really not expert of Linux anyway. The serial console  simulator software I use is minicom.

The symptom is that there is no response. When connected the minicom  shows that it is "Offline". The same console cable and device works on  another serial port so the device and the cable should be good.

 ```
dzhao@Ubuntu:~$ setserial -g /dev/ttyS* | grep -v unknown
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS4, UART: 16650V2, Port: 0xe080, IRQ: 16
/dev/ttyS5, UART: 16650V2, Port: 0xe400, IRQ: 17
/dev/ttyS6, UART: 16550A, Port: 0xec00, IRQ: 18
/dev/ttyS7, UART: 16550A, Port: 0xe880, IRQ: 18
/dev/ttyS8, UART: 16550A, Port: 0xe800, IRQ: 18
/dev/ttyS9, UART: 16550A, Port: 0xe480, IRQ: 18
``` ```
+-----------------------------------------------------------------------+
| A -    Serial Device      : /dev/ttyS8                                |
| B - Lockfile Location     : /var/lock                                 |
| C -   Callin Program      :                                           |
| D -  Callout Program      :                                           |
| E -    Bps/Par/Bits       : 9600 8N1                                  |
| F - Hardware Flow Control : No                                        |
| G - Software Flow Control : No                                        |
|                                                                       |
|    Change which setting?                                              |
+-----------------------------------------------------------------------+
```All other serial ports have the same config. Is there anything else other than hardware problem which could cause this?

Thanks!

---

### Post by huntkey on 2011-12-13
Hey 7777 thank you so much for the quick reply! I use a separate minicom config for ttyS8. Anyway I just tried to set the minirc.dfl to something else but the ttyS8 port still doesn't work. Here is what my minirc.dfl looks like:

```
# Machine-generated file - use "minicom -s" to change parameters.
pu port             /dev/ttyS0
pu baudrate         9600
pu rtscts           No
/etc/minicom/minirc.dfl (END) 

```

I actually can see stuff on the ttyS8 connection. They are console messages. However it is that when I hit enter the console doesn't give me response. Help...

Thanks!

---

