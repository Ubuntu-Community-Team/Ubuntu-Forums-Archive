---
title: "DSL problems"
date: 2006-04-22
forum: General Help
---

### Post by Vulcan on 2006-04-22
For some reason the internet, which is connected to DSL, by Verizon, is not connecting. Yet, my father has a laptop running Windows XP, and the internet is working fine. The Ubuntu internet is directly connected to DSL, while my father's laptop is wirelessly connected to the same DSL connection. What's wrong?

---

### Post by cilynx on 2006-04-22
You're sharing a connection via a DSL router?  That's what it sounds like to me.  Assuming that is the case, does your Ubuntu machine get an address from the router?  Can you ping the router?

---

### Post by az on 2006-04-23
How exactly did you configure your connection?  Did it ever work?

---

### Post by Vulcan on 2006-04-23
[QUOTE=azz]How exactly did you configure your connection?  Did it ever work?[/QUOTE]

I didn't configure it. I just installed Ubuntu some time ago, and it set it up for me.

[QUOTE=cilynx]You're sharing a connection via a DSL router?  That's what it sounds like to me.  Assuming that is the case, does your Ubuntu machine get an address from the router?  Can you ping the router?[/QUOTE]

You are talking to a computer newb. :P I can't connect to the internet at all with my Ubuntu machine.

---

### Post by cilynx on 2006-04-23
So, it never worked?  If you poke around in System->Administration->Networking, what do you find?  Do you have any interfaces listed?  Are they active?

---

### Post by Zyphrexi on 2006-04-23
I know when I set up breezy to use my wireless internet connection, I had to input the essid and network key and set up the gateway as 192.168.1.1 or the name of the router on our network. Occasionally the network-manager is a little wierd, in those instances I crack open a terminal and type

```
sudo ifup ath0
```

though ath0 is the name of my wireless atheros chipset, yours would probably be eth0.

If everything is configured as it should be, doing that should get you net access.
but you probably need your essid and network key at least.

---

### Post by Vulcan on 2006-04-24
[QUOTE=Zyphrexi]I know when I set up breezy to use my wireless internet connection, I had to input the essid and network key and set up the gateway as 192.168.1.1 or the name of the router on our network. Occasionally the network-manager is a little wierd, in those instances I crack open a terminal and type

```
sudo ifup ath0
```

though ath0 is the name of my wireless atheros chipset, yours would probably be eth0.

If everything is configured as it should be, doing that should get you net access.
but you probably need your essid and network key at least.[/QUOTE]

It said something about failing to bring up "eth0".

[QUOTE=cilynx]So, it never worked?  If you poke around in System->Administration->Networking, what do you find?  Do you have any interfaces listed?  Are they active?[/QUOTE]

It seems like they are active, but a modem connection. Though, I'm not using a modem. :P

---

### Post by mjziegle on 2006-04-24
Sounds like your /etc/network/interfaces file is configured wrong.

This is a sample piece of that file for a static IP connection

# The primary network interface
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

Do you have linux drivers for your ethernet card?  What's the output of ifconfig?  Modify /etc/interfaces then do

> sudo /etc/init.d/networking restart

Don't care for the GUI network tools.

All DSL connections in the US use a PPPOE authentication method.  You can either have the router do it or have software on your computer.  Check were the authentication is located.  In most cases it should be on the router, but sometimes you have to configure it using the CDs that come with the router and it install software on your machine.  I suggest doing a little google homework on PPPOE and check the verizon setup.

---

