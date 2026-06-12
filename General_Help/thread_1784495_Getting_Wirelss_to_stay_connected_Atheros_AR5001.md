---
title: "Getting Wirelss to stay connected Atheros AR5001"
date: 2011-06-17
forum: General Help
---

### Post by Robert Butler on 2011-06-17
I have Ubuntu 10.10 on a Toshiba satellite L300 with an Atheros AR5001 wireless network card.
I can get the computer to see the network but it wont persist, it keeps going offline or asking to be re connected. 
Also Firefox will not find the internet even if the wireless icon shows the wireless network is alive.
I can use the laptop for the internet if I plug in the LAN cable but have no luck with the wireless. 
Security for the modem is using WPA&WPA2 and it will connect according to the icon in the title bar for the wireless network.
I have tried the Atheros site for a driver but had no luck finding one. 
Not even sure if that is what I need to do.
Can any one help please
 
More information if its of any use
 
driver=ath5kfriver version=2.6.35-22-genericfirmware=N/A latency=0 link=no multicats = yeswireless=IEEE 802.11bg
 
Also I need to go back to the cause of all of this- I installed new 11.04 and the wirles crapped itself. It had been working beautifully on the previous 10.10 version.
Lesson number 1.
If it aint broke dont fix it.
generic version 2.6 35 28 is what we are booting to

---

### Post by louisgonick on 2011-07-17
> **Robert Butler said:**
> I have Ubuntu 10.10 on a Toshiba satellite L300 with an Atheros AR5001 wireless network card.
I can get the computer to see the network but it wont persist, it keeps going offline or asking to be re connected. 
Also Firefox will not find the internet even if the wireless icon shows the wireless network is alive.
I can use the laptop for the internet if I plug in the LAN cable but have no luck with the wireless. 
Security for the modem is using WPA&WPA2 and it will connect according to the icon in the title bar for the wireless network.
I have tried the Atheros site for a driver but had no luck finding one. 
Not even sure if that is what I need to do.
Can any one help please
 
More information if its of any use
 
driver=ath5kfriver version=2.6.35-22-genericfirmware=N/A latency=0 link=no multicats = yeswireless=IEEE 802.11bg
 
Also I need to go back to the cause of all of this- I installed new 11.04 and the wirles crapped itself. It had been working beautifully on the previous 10.10 version.
Lesson number 1.
If it aint broke dont fix it.
generic version 2.6 35 28 is what we are booting to

I have the same card, and it sucks. I use this to turn it on:
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

Until now I haven't found a solution because each time I reboot the card turns off, but at least it works.

---

### Post by gandaran on 2011-07-18
I have the same card on netbook and works perfectly with the ath5k driver, never had any problem (you can try remove the ath5k driver and install the propitiatory atheros madwifi driver) one question what mode is the wireless connection setup, infrastructure or ad-hoc?

---

