---
title: "Can't connect wirelessly with Ubuntu 10.10"
date: 2011-01-20
forum: General Help
---

### Post by rolling_haro on 2011-01-20
I have a Dell Vostro 1400 with Windows Vista Ultimate.  I've tolerated with the OS long enough and have decided to dual-boot with Ubuntu Linux.  Everything seems to check out except for the network card.  When I check the Wireless Networks tap up top, it says "device not ready (firmware missing)". I've checked everywhere online for solutions, only to find them for older versions of Ubuntu with different laptops.  Thanks, I'm counting on you guys.

---

### Post by Vigh on 2011-01-20
Interesting I have a Dell Vostro and the wireless card just worked straight outta the box, Ubuntu 10.10, you can try opening up a terminal

sudo lshw

that will list all your hardware, identify the wireless network card and let me know what it is, you may or may not need to install drivers for it, if they are even available, most wireless cards just work fresh install

forgot to say- make sure wireless is enabled in the Dell Bios

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by rolling_haro on 2011-01-20
*-network DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:le:8c:10:5c:21
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicase=yes wireless=IEEE 802.11bg

---

### Post by lithopsian on 2011-01-20
The message says it all.  "Firmware missing".  Install the firmware and you should be fine.  I don't 100% understand why this is sometimes necessary and sometimes not.

I don't know exactly which card you have but it thinks the b43 driver is the way to go, so try installing b43-fwcutter which should automatically gibe you the correct firmware for most b43 supported cards.  If not there are more things to try.

---

### Post by rolling_haro on 2011-01-20
Ran B43-fwcutter, but got "Wrong architecture 'i386'".  Well, back to the drawing board.

---

### Post by rolling_haro on 2011-01-20
Ran B43-fwcutter, but got "Wrong architecture 'i386'".  Well, back to the drawing board.

BTW Vigh, which Dell Vostro do you have exactly?

---

### Post by rolling_haro on 2011-01-20
Ran B43-fwcutter, but got "Wrong architecture 'i386'".  Well, back to the drawing board.

---

### Post by rolling_haro on 2011-01-20
Ran B43-fwcutter, but got "Wrong architecture 'i386'".  Well, back to the drawing board.

BTW Vigh, which Dell Vostro do you have?

---

### Post by Spyderkid on 2011-01-20
Could you run 

lsusb

---

### Post by lithopsian on 2011-01-20
Is that a 64 bit laptop?  Do you have a 64 bit Ubuntu installed?

---

### Post by lithopsian on 2011-01-20
Is that a 64 bit laptop?  Do you have a 64 bit Ubuntu installed?

---

### Post by Vigh on 2011-01-21
nah just a stock standard celeron laptop vostro, with 32-bit installed

---

