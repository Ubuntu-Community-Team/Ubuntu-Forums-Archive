---
title: "wpa_supplicant doesnt renew ip address when changing networks"
date: 2006-02-24
forum: General Help
---

### Post by sound_dezign on 2006-02-24
I have several networks at work, each with several access points connected to them. They are all WPA encrypted which is why I'm using wpa_supplicant with my Atheros PCMCIA wifi card.

I use the wpa_cli to select the access point to connect to by typing, for example "select_network 1". It then reassociates with that network as it should. The only problem is that the IP address never gets renewed when changing from one network  to the other.
[SIZE="3"]
[COLOR="Blue"]Can someone tell me if there is a way to get wpa_supplicant to renew its IP everytime it connects to a different AP?[/COLOR][/SIZE]

My way around this is to kill the dhclient3 process and start a new one to get assigned the appropriate IP from the dhcp server on each network.

I'm running ubuntu 5.10, linux-image-2.6.12-10-686, linux-restricted-modules -2.6.12-10-686 and wpasupplicant0.4.5-0ubuntu1. wpa_supplicant is started in /etc/network/interfaces by means of preup.

---

