---
title: "all ports on bittorrent are closed"
date: 2011-04-21
forum: General Help
---

### Post by masterrob213 on 2011-04-21
they ae all closed and i don't know what to do about it

---

### Post by Slim Odds on 2011-04-21
If you're behind a router, you need to route some port to your local computer.

---

### Post by GameboyRMH on 2011-04-21
> **Slim Odds said:**
> If you're behind a router, you need to route some port to your local computer.

That's assuming the computer's local firewall isn't blocking the ports...

---

### Post by Slim Odds on 2011-04-21
> **GameboyRMH said:**
> That's assuming the computer's local firewall isn't blocking the ports...

That is correct.

Most people who have this problem, have a router that is not letting the port through.

---

### Post by yetiman64 on 2011-04-22
> **GameboyRMH said:**
> That's assuming the computer's local firewall isn't blocking the ports...

Ubuntu's firewall (UFW) is disabled by default.

If you are unsure OP use in terminal,
```
sudo ufw status
```You will need to access the web interface for your router and find the port forwarding tab (sometimes called virtual servers) and forward the port for your torrent client to your machines IP.

---

### Post by masterrob213 on 2011-04-22
so how exactly could i go through getting the router to do what i need to?

---

### Post by techunit on 2011-04-22
You likely can't. I say this because most public routers block the use of bit torrents. If this is your own router. Do a search for the router find its IP and set the firewall to off. The point of a firewall on a router is quite inefficient as it doesn't get updated, and really is a static rather than an actuall firewall.

---

### Post by masterrob213 on 2011-04-22
im confused how can i serch for my ip and so is there a way i can use bittorrent?

---

### Post by yetiman64 on 2011-04-22
> **masterrob213 said:**
> im confused how can i serch for my ip and so is there a way i can use bittorrent?

Find the IP with the command ```
route
``` in terminal. An example with the IP needed highlighted from this machine is below. > :~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         192.168.1.1     0.0.0.0         UG    0      0        0 br0
default**         192.168.1.1**     0.0.0.0         UG    100    0        0 br0
 This is the IP to enter in the address bar in firefox to access the routers config. You will need to know the username and password for the router - refer to its documentation for that. Once logged in look for settings regarding forwarding or virtual servers.

I for one _don't_ recommend you drop the hardware firewall. Remember, Ubuntu doesn't turn on its firewall by default, and if you have enabled any programs that listen for incoming connections (open a port) you will be exposing them to the internet.

Edit: your machines IP can be found in network manager in "connection information". I'm unsure where that is found as I use the "wicd" network manager.

---

### Post by Slim Odds on 2011-04-23
It's NOT a firewall problem, it's a PORT FORWARDING problem.

You might need to read the manual for your router.

---

### Post by ububeginner on 2011-04-23
This site provides instructions on how to open ports on most routers
[http://portforward.com/](http://portforward.com/)
The guides are windows based (finding your ip and setting a static one) but accessing the router with a browser is OS independent.

---

