---
title: "how to make network manager visible?"
date: 2011-04-23
forum: General Help
---

### Post by psihokiller4 on 2011-04-23
I have Wlan available but I cannot connect to it
I don't have wire network available so I can't connect to internet at all

I'm writing this trough dual boot (win)

how to make network manager visible so I can choose witch Wlan connect to?

I already tried some things here: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)


SOLVED:
> **gandaran said:**
> 
if the network manager panel icon is missing all you have to do to get  it back is right click on the empty panel area where you want it to be,  choose add to panel and select the notification area applet and click  add.

---

### Post by gandaran on 2011-04-23
> **psihokiller4 said:**
> I have Wlan available but I cannot connect to it
I don't have wire network available so I can't connect to internet at all

I'm writing this trough dual boot (win)

how to make network manager visible so I can choose witch Wlan connect to?

I already tried some things here: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

the wireless networks should be visible, maybe you need to install a wireless drivers first, hook up the laptop to cable internet and run the software list update commamd
```
sudo apt-get update
```
then look in system » administration » additional drivers for wireless card driver and enable it.
if no driver there post the output of these commands so we can check what brand of wireless card.
```
lspci
```
and 
```
lsusb
```

---

### Post by psihokiller4 on 2011-04-23
uh nice thanks

will try to tipe output text as much as I could remember it :P


I have no cable available for more 1 week :S
this network manager was usually available at home so I don't know what's wrong
I'll try to get out put

---

### Post by gandaran on 2011-04-23
> **psihokiller4 said:**
> uh nice thanks

will try to tipe output text as much as I could remember it :P


I have no cable available for more 1 week :S
this network manager was usually available at home so I don't know what's wrong
I'll try to get out put
you mean network manager worked before? is the network manager icon missing from the panel? is this the problem you are referring to?

---

### Post by psihokiller4 on 2011-04-23
ok just remembered Ii can mount win partition

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
```



```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by psihokiller4 on 2011-04-23
> **gandaran said:**
> you mean network manager worked before? is the network manager icon missing from the panel? is this the problem you are referring to?


exactly

and I need it to choose witch wireless I want to connect to

I can't find it in menu but network connections is not it
yes that icon on pannel


EDIT:
PS. I have at startup app enable the network manager

---

### Post by gandaran on 2011-04-23
> 01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
no need to install driver for this card, it works out of the box.
if the network manager panel icon is missing all you have to do to get it back is right click on the empty panel area where you want it to be, choose add to panel and select the notification area applet and click add.

---

### Post by psihokiller4 on 2011-04-23
thank you very very very much writing from Linux \o/


SOLVED :)

---

