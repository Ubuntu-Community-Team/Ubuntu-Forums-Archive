---
title: "Absolutely cannot get good DL speeds"
date: 2011-06-07
forum: General Help
---

### Post by griffsterb on 2011-06-07
I'm at the end of my patience. I have tried both Transmission and Deluge torrent apps, and tried a torrent with 3000 seeds that was just uploaded yesterday. In windows I typically get 700kB/s to 1.5MB/s speeds on these torrents. 

In ubuntu with either client I cannot get above 60 or 70 kB/s. I've had one or two torrents that have shown flashes around 500kB/s but almost ALWAYS ridiculously slow speeds.

Is there anything I can do?

---

### Post by Mark Phelps on 2011-06-07
One thing you could try is upgrading the network card/chip driver.

Use lspci to find out the make/model of your network card/chip.

Then go to the manufacturer's website and see if they provide Linux drivers.  If they do, they will also provide instructions on how to compile the drivers into a kernel module and how to install it.

I used a Marvell network chip on my previous PC and they were pretty good about providing Linux drivers.

---

### Post by pqwoerituytrueiwoq on 2011-06-07
the torrent could have poor seeding
anyway nets make sure not network card it behaving
[FONT=Courier New]echo "Please wait..."; ping 192.168.1.1 -c 10 | grep "packet loss"[/FONT]

to verify that is the right address
[FONT="Courier New"]ifconfig | grep "inet addr:"
          inet addr:**10.0.0.50**  Bcast:10.0.0.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
i would use [FONT="Courier New"]echo "Please wait..."; ping 10.0.0.1 -c 10 | grep "packet loss"[/FONT]
if it does not say 0% and there is either a faulty network card or a bad driver

---

### Post by emarkay on 2011-06-07
Also, OP, please do tell your hardware info. 

I still have 2 PCs, identical software, different hardware where one (this one) has an onboard LAN that never gives full DL speeds, even when I can test its potential at capacity successfully (DL "speed testers") . It's a known issue with the SiS 900 series. BTW)

---

