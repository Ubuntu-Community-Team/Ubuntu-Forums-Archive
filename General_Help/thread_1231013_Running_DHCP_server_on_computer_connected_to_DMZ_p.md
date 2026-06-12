---
title: "Running DHCP server on computer connected to DMZ port of router. Is it safe?"
date: 2009-08-04
forum: General Help
---

### Post by MaxIBoy on 2009-08-04
I was thinking about running PXE on my home server. A lot of people lend me computers so I can clean them up, and booting from CDs is getting old. Unetbootin is nice but a lot of older computers can't boot from flash drives, and I usually need my flash drives for other uses. Anyway, physical objects are passé, so being able to use network boot instead would be nice.

However, from what I've read, in order to enable network boot I'd have to disable the DHCP functionality of my router and run DHCP on the server instead. I'm pretty sure I'd be able to get that set up without too much trouble, but for various reasons my home server is on the DMZ port of my router.

What I'm worried about is someone outside the network, gaining an IP address from the home server and then circumventing the security on the other computers in the house. Besides the server, I have two Linux boxes which haven't been "hardened" the same way the server has. But of special concern is my parents' XP box, which will basically trust anything on the same LAN as it. And despite my protests, they keep all their passwords in an Excel file called "passwords.xls," how obvious is that?

Is this something I need to be worried about? Are there any security risks I could expose myself to from this?

---

### Post by thisllub on 2009-08-04
Why aren't you using port forwarding?

---

### Post by MaxIBoy on 2009-08-04
The server is on DMZ because it's hosting a game server. My router (cheap Linksys) has port forwarding options in its configuration menus, but as far as I could tell these options did nothing. So I put the server on DMZ and setup the iptables configuration to allow the ports used by the game, as well as ssh, and then block all other ports.

---

### Post by thisllub on 2009-08-04
It is all relative.
If your firewall is configured correctly you should have no problem but surely port forwarding can work for the game services?

Of course you could always run up a virtual machine for the game server and put that in the DMZ.

---

### Post by MaxIBoy on 2009-08-04
I'm sure that if I tried I could get the router to forward the right ports. However, the router's configuration tools were very confusing, and I really could not get *any* results from them (no one outside my LAN could join the game server, also telnet reported that the ports were closed.) After about a day of tinkering with it, I moved the server to DMZ, setup iptables, and twenty minutes later it worked. 

Anyway, If I have to disable DMZ in order to run DHCP on my server in a secure way, I'm sure I can get it to work. But do I have to disable DMZ for it to be secure?

By the way, I doubt the server could run a VM with enough performance to do anything useful. 128 mb RAM and a Pentium II.

---

