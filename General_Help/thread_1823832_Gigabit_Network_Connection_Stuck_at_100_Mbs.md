---
title: "Gigabit Network Connection Stuck at 100 Mb/s"
date: 2011-08-12
forum: General Help
---

### Post by lakerssuperman on 2011-08-12
I have a machine with an MSI motherboard and gigabit ethernet.  However, it only reports being connected at 100Mb/s.  I have tried using ethtool to force the speed to gigabit but it doesn't seem to have any effect.  I'm using Ubuntu 11.04.  Does anyone know a way other than ethtool to set the network speed?  Help is much appreciated.

---

### Post by bkratz on 2011-08-13
> **lakerssuperman said:**
> I have a machine with an MSI motherboard and gigabit ethernet.  However, it only reports being connected at 100Mb/s.  I have tried using ethtool to force the speed to gigabit but it doesn't seem to have any effect.  I'm using Ubuntu 11.04.  Does anyone know a way other than ethtool to set the network speed?  Help is much appreciated.



First I would make sure that I had cabling that would handle the speed. Cat5 is not rated for that. It would take at least cat5e or cat6 to reach that speed, (except maybe very short runs).

---

### Post by JonasPed on 2011-08-13
It might also be a help to know the chip on the NIC and the command you are using to force it to 1GB.

---

### Post by mcduck on 2011-08-13
> **lakerssuperman said:**
> I have a machine with an MSI motherboard and gigabit ethernet.  However, it only reports being connected at 100Mb/s.  I have tried using ethtool to force the speed to gigabit but it doesn't seem to have any effect.  I'm using Ubuntu 11.04.  Does anyone know a way other than ethtool to set the network speed?  Help is much appreciated.

What speeds the other devices on your network support? The network speed is always determined by the slowest connected device (And all the cables must support the same speed as well, of course).

---

### Post by lakerssuperman on 2011-08-14
I tried several different brand new cables Cat 5e.  The router is right next to the computer so it is also a very short run.  The network chip is the onboard LAN found on this board.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130560](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130560)

The command I'm using to set the speed I got from this page and just changed the numbers accordingly.

[http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html)

Finally, the other machines on the network are two HTPC's hooked in both with gigabit hardware.

---

### Post by lakerssuperman on 2011-08-14
I posted the wrong motherboard link.  It is actually the 760GM-E51.

Under connection information in the Network Indicator, it reports that it is using the r8169 driver.

---

### Post by pqwoerituytrueiwoq on 2011-08-14
do you have a gigabit router/switch?

---

### Post by lakerssuperman on 2011-08-14
Yes it is a brand new Netgear WNDR3400.

---

### Post by pqwoerituytrueiwoq on 2011-08-14
> **lakerssuperman said:**
> Yes it is a brand new Netgear WNDR3400.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122378](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122378)
if that is your router that is NOT a gigabit Ethernet router
i would suggest getting gigabit switch to but behind yuor router if you need a local gigabit connection
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704042](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704042) (cheapest one on newegg atm)

---

### Post by lakerssuperman on 2011-08-14
My apologies.  I thought I had read that it was as I have the WNDR3700 at my house and that one is Gigabit.  At least I know it wasn't something not configured correctly.

---

