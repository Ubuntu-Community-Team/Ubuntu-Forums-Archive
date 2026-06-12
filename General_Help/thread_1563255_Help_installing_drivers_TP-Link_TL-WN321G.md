---
title: "Help installing drivers TP-Link TL-WN321G"
date: 2010-08-28
forum: General Help
---

### Post by ianbcal on 2010-08-28
I am pretty new to Linux and can get around, but i have not mastered the finer art of installing drivers. I am trying to install a tp-link wireless adapter tl-wn321g which are green lighted but since i don't know how to install the driver i am stuck. HHHEEEEELLLLLPPPP:confused:

---

### Post by Mark Phelps on 2010-08-29
Are these MS Windows drivers that come with the product? If so, you can't install them as they are not Linux drivers.

If you check in the Networking forum and do a search using your device model number, you may find some threads where folks have succeeded in getting that device to work using alternate approaches.

---

### Post by maldonado82h on 2010-08-30
The last versions of ubuntu already have a working driver. I have a TPlink wireless adapter like yours

---

### Post by 48X24X48X on 2010-10-31
Being a Linux newbie, I'm facing a same problem too. I know that the latest version has the necessary drivers but I'm getting some error message like:

```

[    7.784807] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[    7.784874] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.

```

I did managed to get connected to the WLAN only twice. But, I'm not sure what triggered it take place. Is there a better solution than installing ndiswrapper? Thank you.

---

### Post by itsales on 2010-11-01
> **maldonado82h said:**
> The last versions of ubuntu already have a working driver. I have a TPlink wireless adapter like yours
But TP-Link TL-WN321G cannot use like other model:confused:

---

### Post by bernax2 on 2010-11-17
Mannn,  I have the same problem with the default driver (rt2800), I get the connection icon that is already connected to the network, but my router says I'm not connected (my bg protocol router has 3 lights, power, broadband link and network) so the network light is not lit, - formerly sometimes with the wired connection was lit in orange color (green is good, orange is a warning) said they had connection but there was a problem, in this particular case with the USB adapter, the adapter LED is blinking but not the router ...
 
Note: Using WinXP in the same PC the usb adapter works great, i think this is a driver problem...

---

### Post by Vigh on 2010-11-17
hello,
    you shouldn't have to install any drivers, if its not connecting properly, setting up a static network may help, that is DHCP is turned off on the router and all devices in the network have static IPs with the IP number, subnet, gateway and DNS inputted manually into ubuntu, I am use DHCP at home, but had to manually set up a static network for my sister which solved her network problems with regards to a realtek chip,

what does this command report when you enter it in the terminal->

sudo lshw -short

---

