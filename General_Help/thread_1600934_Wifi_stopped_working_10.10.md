---
title: "Wifi stopped working 10.10"
date: 2010-10-19
forum: General Help
---

### Post by ki4jgt on 2010-10-19
I have an atheros wifi card and last night my computer froze and my hard drive would not stop running. turned it off with the button. When it came back on, my wifi wouldn't work. I've tried everything I can think of sudo killall networkmanager (no such process) deleted Gnome settings folders in Home. No luck.

Also tried network-manager

**EDIT: The thing keeps disabling the Wireless. I'm hooked into the eithernet right now. But when the wireless isn't disabled, I try to create a network or connect to a hidden network and it disables my wireless altogether. It doesn't even allow it to be re-enabled even after I reboot. I have to completely shut down.

---

### Post by Linye on 2010-10-19
Did you try right click on the applet and check "enable wireless" ?

---

### Post by ki4jgt on 2010-10-19
It wont let me. When it disables it, it removes it from the list or it blacks out the words so you can't click on them. I've had 10.10 for three weeks and it's worked fine.

---

### Post by Hippytaff on 2010-10-19
Might it be a driver conflict?

what wireless is it

```

lspci

```

---

### Post by ki4jgt on 2010-10-19
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

---

### Post by Hippytaff on 2010-10-19
> 
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


this is your chipset etc mighty be worth reading this...
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by mchristian on 2010-10-19
Same thing happen to me.  I have a Broadcom 4318.  I did a re-install and it has not happen again , yet.  When it did happen I was working with an upgrade from 10.04, but now it is a fresh install.  No problems so far.  But originally I had no problem with the upgrade either.

---

### Post by Hippytaff on 2010-10-19
> **mchristian said:**
> Same thing happen to me.  I have a Broadcom 4318.  I did a re-install and it has not happen again , yet.  When it did happen I was working with an upgrade from 10.04, but now it is a fresh install.  No problems so far.  But originally I had no problem with the upgrade either.

I think its something to do with conflicting drivers

---

### Post by joe.malachowski on 2010-10-19
Try installing, updating the brodcom driver. alot of wireless adapters conflict with  Ubuntu 10.10 and that is ussaly the fix.

---

### Post by ki4jgt on 2010-10-19
I don't get why I need to do this. I haven't had a problem in three weeks. I did a hard shut down and the problem started. Are you sure this is the solution?

---

### Post by ki4jgt on 2010-10-19
Sorry didn't see you there Joe. I haven't got any drivers. I haven't needed them so where do I get them?

---

### Post by ki4jgt on 2010-10-19
Prayed over it! fooled around with the Wifi switch which Ubuntu does not support after a clean start up everything returned to normal. I think the switch may be able to work with the hardware, even though Ubuntu doesn't officially recognize it. I may have been playing with it last night. But it didn't stop working until a few mins after I had messed with it. I think I've had this problem before, but due to Ubuntu not being able to recognize the switch it doesn't register with that the Wifi is on/off until Ubuntu is completely shut down. So after a few minutes, the hardware stopped respnding to Ubuntu and when I shut it down, it became official. Thank God for showing me that one, b/c it was a total miracle.

---

