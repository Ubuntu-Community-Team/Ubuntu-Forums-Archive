---
title: "wireless troubles: cannot get it to work"
date: 2006-05-08
forum: General Help
---

### Post by Polygon on 2006-05-08
Ok i am a linux newbie. bear with me

My wireless network card is [THIS]("http://www.dlink.com/products/?sec=0&pid=422") (DWL-G520M), and i believe it uses the Atheros chipset. 

I have recently done a reformat of the hard drive that Ubuntu 5.10 was on because i had nothing important on it, and i reinstalled ubuntu 5.10.

The only thing i have done so far is try to get it working using ndiswrapper. I downloaded ndiswrapper-utils, and tried it, didnt work. So i removed ndiswrapper and ndiswrapper-utils and followed a wiki's instructions and downloaded and compiled the newest version (1.16) and it still does not work

I would like suggestions On how to get my damn wireless to work. I have tried ndiswrapper, and using MadWiFi except that MadWiFi was not working or something because after i installed them, it was suppost to create ath0, but it kept saying "no such device"

In both ndiswrapper and MadWiFi it says that the DWL-G520 works, but nothing on the DWL-G520M

any help? please?

---

### Post by skippy81 on 2006-05-08
Open a terminal and do a > lspci and copy the text to this forum.  

You best bet would be to download the linux-restricted-modules package for your kernel and modprobe the atheros driver:

> sudo modprobe madwifi-ng

or 

> sudo modprobe madwifi

Once its modprobed then 

> ifconfig ath0 up

If this doesnt work then I would say your out of luck i'm afraid.  If your sure you loaded the madwifi driver correctly the first time round, then I can't really see the situation improving im afraid.

---

### Post by Polygon on 2006-05-10
Im actually getting a new wireless card (one that is actually suppost to be supported) but im still confused on how to download the linux-restricted-modules package, how do i do this?

and once i download this package, do i use synaptic to install madwifi?

---

### Post by mjziegle on 2006-05-10
sudo apt-get install linux-restricted-modules

Don't use ndiswrapper.  

Post the output of lspci -v so I can make sure you have an atheros card.

Then post /etc/network/interfaces

I'll get you up and running if you have an atheros card.  Send me a PM.

I haven't been able to get WEP to work from the install on Dapper, no encryption installs work fine.  If you don't setup the wireless on installation you have to edit /etc/network/interfaces

-matt

---

### Post by Polygon on 2006-05-10
well... what happens if i need to have wep working? 

whatever, ill come to that when i come to it, you know off hand what i have to edit for ubuntu to see my new wireless card?  my card hasnt come in yet, i think tommrow it will though) but im pretty sure its an atheros chipset, cause according to this site ([clicky]("http://linux-wless.passys.nl/query_chipset.php?chipset=Atheros&zoek=Show") the "DWL-G520" is listed (i searched for atheros chipset) and it says the driver is madwifi.

---

### Post by mjziegle on 2006-05-12
WEP works fine after the install.  It just requires some modification to /etc/network/interfaces.

I haven't been sucessful with WPA and this card.

-matt

---

