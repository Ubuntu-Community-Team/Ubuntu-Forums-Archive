---
title: "Natty - wireless not connecting"
date: 2011-08-11
forum: General Help
---

### Post by goldlinux on 2011-08-11
Sorry people if here is not the right place to post this message. I've seen lots of people with problems in the wireless but not exactly mine.

Well, the problem is, I can see all the networks around me, but I can't connect to them. when I click on my wireless network to connect, it stops when is getting the ip (from the dhcp server in the modem) and it doesn't connect, doesn't show any message, anything.

But different as I've seen from another posts my K/Ubuntu don't freeze.

When I was with Kubuntu 10.08 everything was working but now I am using Kubuntu 11.04 on the same notebook, HP Pavilion dv6 and the wireless not connect. 

lspci -nnv | grep Wireless
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

And using the driver ath9k.


Thank you guys.

---

### Post by Bart92 on 2011-08-11
> **goldlinux said:**
> Sorry people if here is not the right place to post this message. I've seen lots of people with problems in the wireless but not exactly mine.

Well, the problem is, I can see all the networks around me, but I can't connect to them. when I click on my wireless network to connect, it stops when is getting the ip (from the dhcp server in the modem) and it doesn't connect, doesn't show any message, anything.

But different as I've seen from another posts my K/Ubuntu don't freeze.

When I was with Kubuntu 10.08 everything was working but now I am using Kubuntu 11.04 on the same notebook, HP Pavilion dv6 and the wireless not connect. 

lspci -nnv | grep Wireless
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

And using the driver ath9k.


Thank you guys.

I have also the same problem with my Hp pavilion dv6 in Ubuntu 11.04 i think its just a driver problem

>> [http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)  <<

---

### Post by Kira_Belka on 2011-08-11
how about madwifi drivers?

---

### Post by rizman on 2011-08-11
I had issues connecting to my WiFi network too so I'm posting this in case it helps. 

I was able to see my network, but when trying to connect, I ended up in an endless loop where I was being asked my Passphrase for the network. However, I could never connect. It is a WPA2 encrypted network.

Anyway, what helped me was to change the "Channel Width" setting on my wireless router from "Auto 20Mhz/40Mhz" to "20Mhz". (It's a D-Link DIR-635. Don't know if other brands have this option too. I don't even know what it does. It just seems to work now)

Might be worth a shot.

My WiFi Chipset is the Intel WiFi Link 5100.

Also on Ubuntu 11.04

---

### Post by MARP1961 on 2011-08-11
I have encountered problems similar to this in Ubuntu and have got round it by deleting the keyring password (well actually you select a blank password and save as 'unsafe').

The following guide is written for Gnome desktop; but if you know how to get to the passkey/encryption section of the menu in the Kubuntu KDE menus it should work in a similar way. Also you need to edit your wi-fi router entry in the Netwok Manager to select 'All Users'. [HTML][/HTML]
[http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu](http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu)

---

### Post by Kira_Belka on 2011-08-11
I had same prob on atheros 5002 ( it was ubuntu netbook 10.04).. madwifi drivers and firmware from backtrack 4 helped me last time

---

### Post by Kira_Belka on 2011-08-11
and my advice.. it's my experience says  it 'll better to remove Network manager and to configure your wifi using iwconfig/ifconfig commands

---

