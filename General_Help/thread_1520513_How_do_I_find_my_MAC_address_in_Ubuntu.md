---
title: "How do I find my MAC address in Ubuntu?"
date: 2010-06-29
forum: General Help
---

### Post by Nick_Jinn on 2010-06-29
I have comcast. If I plug it directly into the modem, how do I discover my MAC address?

---

### Post by supergrav on 2010-06-29
Running ifconfig doesn't give you MAC address?

---

### Post by Nick_Jinn on 2010-06-29
I havnt tried. Is that how I do it?

From the command line or is that a program?

---

### Post by supergrav on 2010-06-29
Enter a terminal and run ifconfig. This will give you all your network interfaces with their details. MAC address is shown as HWaddr: XX:XX:XX:XX:XX:XX.

---

### Post by indBcode on 2010-06-29
```
arp -n

``````

Address                  HWtype  [COLOR=Black]**HWaddress** [/COLOR]          Flags Mask            Iface
192.168.1.254            ether   [COLOR=Red]**02:5f:64:70:71:29**[/COLOR]   C                     eth0
```

---

### Post by Nick_Jinn on 2010-06-29
indBcode, do you use comcast?


Thanks. Thats a big help.

Can I still get my mac address even if I am plugged into a router or do I need to plug directly into the modem?

---

### Post by mhgsys on 2010-06-29
```
ifconfig | grep HWaddr
```
will give MAC of internal hw.
{eth0 wlan0 etc

```
arp -n
``` 
will give mac of external hw

{modem/router,etc

---

### Post by sgosnell on 2010-06-29
Which MAC address do you need, and why?  The MAC address of a hardware device never changes, it's always the same.  Your computer and your router have different MAC addresses, and your computer has a different MAC for the ethernet and wireless cards.  iwconfig will give you the address of the router or modem, ifconfig will give you the address of your ethernet and wireless cards, and they are different.  You can also right-click on the network manager icon in the panel, select Connection Information, and that will give you the MAC (hardware address) of the active network card.

---

### Post by Nick_Jinn on 2010-07-13
Awesome.

I am trying to test the true speeds for this line. All I need is another Mac Address from someone else on a different node and I can finish my experiment.

---

