---
title: "Network Command-Line Tools"
date: 2010-05-28
forum: General Help
---

### Post by Kerubu on 2010-05-28
Hi,

I'm trying to educate myself about networks and would like to know if there are any command line tools which I can use to investigate my own network. All I read so far is about pinging and DNS lookups for remote servers, but can't seem to find out how to query my own wireless network !

For example, taking my own set up, I have a wireless-adsl modem which I use to connect several computers to the internet (and each other if I desired). Naturally when I installed the modem I needed to name the wireless network which I have done so to 'Flintstone' (names changed to protect the innocent!). So how could I, using COMMAND LINE INSTRUCTIONS :

1. first of all discover what networks are available i.e. what's detected by my wireless or ethernet card.
2. Once connected on 'flintstone', find out what else is connected to that network.

I'm not even sure command line tools that would allow me to do these things exist.

Cheers

Kerubu

---

### Post by inso_741 on 2010-05-28
why dont you try aircrack-ng?
it has tools for monitoring the network

---

### Post by Kerubu on 2010-05-28
> **inso_741 said:**
> why dont you try aircrack-ng?
it has tools for monitoring the network

Thanks inso_741,

Are there any general Linux CLI tools though, not just for wireless networks ?

---

### Post by inso_741 on 2010-05-28
nmap - commandline port scanner
iptraf - Packet analysis
tcpdump - advance user only
ethereal - graphical expression of tcpdump 
etherape - graphical traffic analyzer

---

