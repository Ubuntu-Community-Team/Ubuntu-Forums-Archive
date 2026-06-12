---
title: "(Easy Question) How to add internet to UBUNTU SERVER?"
date: 2010-10-02
forum: General Help
---

### Post by Manifest on 2010-10-02
Yup the title explains it all.
so im a complete noob to Server.
How do I add internet connections to Ubuntu Server?:KS

---

### Post by envygeeks on 2010-10-02
The title doesn't explain "it all", please elaborate better "add internet."
For example, are you using DHCP? Are you using static configurations?
Do you even have public facing access? Are you in a data centre or at home?

---

### Post by Manifest on 2010-10-02
i need to add my router so it can access the internet
And please don't get bitchy and I wont be bitchy to you

---

### Post by btindie on 2010-10-02
*envygeeks* wasn't being bitchy, he was simply stating that for people to provide you with help you need to give more detailed information as to your problem because at the minute your question is too general - the more information you provide the easier it is to help. At the minute it's hard to know where to start.
 
Does [this]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") help you with your problem?

---

### Post by yaztromo on 2010-10-02
Assuming your network card is eth0:

sudo nano /etc/network/interfaces

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
	address 192.168.0.249
	netmask 255.255.255.0
	gateway 192.168.0.1

```

In that instance I've made the IP for my server 192.168.0.249. The router IP is 192.168.0.1. Change it to your needs.

Then edit /etc/resolv.conf and add your DNS server (probably your router IP)

sudo nano /etc/resolv.conf

```

nameserver 192.168.0.1

```

Reboot and see what happens. This is all assuming you have network card installed and working. It's difficult to tell from your post exactly what stage you are at.

You can test the connection from your server by pinging something, for instance:

ping [www.yahoo.co.uk](www.yahoo.co.uk)

---

### Post by mikewhatever on 2010-10-02
Easy question? What, to ask or to answer?

---

### Post by Manifest on 2010-12-12
Thanks, but could you do this with wlan0?

---

### Post by CharlesA on 2010-12-12
> **Manifest said:**
> Thanks, but could you do this with wlan0?
You'd need to add the ESSID and encryption key to the interfaces file.

See [here]("http://modelr.wordpress.com/2009/06/01/how-to-get-wireless-network-on-ubuntu-server/"). 

I recommend servers have a wired connection, not wireless, but it's your choice. :)

---

