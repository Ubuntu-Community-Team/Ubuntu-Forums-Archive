---
title: "How to enable wireless networking?"
date: 2010-06-13
forum: General Help
---

### Post by kommunisti on 2010-06-13
When i click the network manager icon it just says under wireless networks "Wireless network is not enabled" How do i enable it? It is just grayed out.

---

### Post by cogier on 2010-06-13
I think you need to provide a lot more detail to allow people to help.

What version of Ubuntu are you using?
What computer are you using?
Did it work before?
Do you know the type of Wi-Fi card your computer uses.

---

### Post by RJ12 on 2010-06-13
Have you tried right clicking it and checking "Enable Wireless"? Also if you have a laptop, does it have one of those wireless switches that enable/disable wireless?

---

### Post by kommunisti on 2010-06-13
> **RJ12 said:**
> Have you tried right clicking it and checking "Enable Wireless"? Also if you have a laptop, does it have one of those wireless switches that enable/disable wireless?

Right clicking is also grayed out, i have a laptop, ASUS PRO50GL. Yes it has a switch, which does nothing. It didn't work before, im using 10.04 Lucid Lynx.

WiFI card:

```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a3b:1067
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

---

### Post by kommunisti on 2010-06-13
Bump

---

### Post by kommunisti on 2010-06-14
Bump

---

### Post by fooman on 2010-06-14
have you checked in system > administration > hardware drivers

to see if there is a driver available?  if there is a driver listed,  click on it then click activate.

---

### Post by kommunisti on 2010-06-14
> **fooman said:**
> have you checked in system > administration > hardware drivers

to see if there is a driver available?  if there is a driver listed,  click on it then click activate.

Only my Nvidia drivers are listed.

---

### Post by kommunisti on 2010-06-14
Desperate bump :confused:

---

### Post by kommunisti on 2010-06-14
bump

---

### Post by kommunisti on 2010-06-14
bump

---

### Post by someonenew on 2010-06-14
have you tried sudo ifconfig wlan0 up ?

---

### Post by DrDunkMcNally on 2010-06-21
Hey,

Same problem as kommunisti.

Computer is HP Pavillion tx 2000. Unsure how to check in terminal what network card is being used.

however, I tried sudo ifconfig wlan0 up and got

wlan0: ERROR while getting interface flags: No such device.

The laptop does have a wireless switch, which is inactive (when I push it to the side it doesn't respond).  Also the switch is spring-loaded so always returns to it's original position. Could the switch be the problem?

thanks for any help.

*edit*: my network controller as listed using the lshw command in terminal is "Broadcom BCM4322 802.11a/b/g/n Wireless Lan Controller"

**edit**: after plugging in an ethernet cable and doing all the necessary updates from a fresh install i was able to use a proprietary driver and activate my wireless. also the wireless switch is now fully functional.  Sorry I couldn't be of any help!

---

