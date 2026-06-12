---
title: "Internet not working- DNS"
date: 2006-04-22
forum: General Help
---

### Post by hey_joe42 on 2006-04-22
hi, Just got Linux Ubuntu and trying to figure out how to setup the internet
I have the subnet, gateway and ip address setup, the same as my xp set up, but i cna't figure out how to tell it my 2 dns #'s that my xp has.

---

### Post by Ramses de Norre on 2006-04-22
system > administration > networking > DNS tab

---

### Post by jazzmuzik on 2006-04-22
Usually your modem/router inserts the values into /etc/resolv.conf automatically. Otherwise, try System, Adminstration, Networking, DNS.

You could also try adding the values manually with an editor:

gksudo gedit /etc/resolv.conf

Enter something like this:

search earthlink.net
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

You might look at the "Connections" tab and the Properties for your net connection. If your address is assigned via your isp/modem make sure it is set to DHCP. I mention this because the DNS setup should be automatic, but it's not in your case for some reason.

---

### Post by hey_joe42 on 2006-04-24
alright, im very new to this ubuntu, im trying it out, and figured if i can get the internet on it, i can figure out the rest.
Im used to windows
to configure the internet on my windows i do this.
- go to control panel>network connections>click on properties of my tcp connection>
Click on the button for 'use specified ip address'
type in 192.1681.6
subnet 255.255.255.0
gateway: 192.168.1.1
use the following dns server addresses
206.48.122.2
206.48.122.8


so for my linux i went ot configuration as a static IP address entered the ip, subnet and gateway the same
now its the dns causing me problems
I have entered them as dns servers, but still no internet connection

---

