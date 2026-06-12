---
title: "linux and attglobal.net"
date: 2006-05-26
forum: General Help
---

### Post by cssutto on 2006-05-26
I have tried to set up with attglobal.net with no luck.

I did find that they have a dialer software, which I downloaded.

It put a file on my Desktop which I can do absolutely nothing with.

It is names "setup".

In the properties window, it shows the desktop location and "application/x-executable"

I hae tried various ways of opening it, but I am not linux smart enough to install it.

Does anyone have any advice?

There is no doubt this is a real exec file because its size is 7.6MB.

I have given everyone permissions, so it is not a permission problem.

CSSJR

---

### Post by mjziegle on 2006-05-27
Ddit /etc/network/interfaces

Add the following lines and remove all others that reference "eth0"

iface eth0 inet dhcp
auto eth0

then 

sudo /etc/init.d/networking restart

You then need to configure (make sure) your modem does PPPOE on the modem.  Go to 192.168.0.1

Select PPPOE location and pick on the modem.  Enter your login name and password or make sure that you are synched up.

You don't need any crappy software.

You have DSL right?

Dial-up 

Install gnome-ppp from synaptic and use that.

---

### Post by cssutto on 2006-05-27
No, I don't need any crappy software except for one minor thing.

I have two ISP's.  They are both dial-up because even though I am in a relatively modern civilized area, North Carolina, USA, until recently DSL was not available at either my home or office location.

The other ISP works.  However it does not have as many nodes and is not as reliable as attglobal.net.

I have an order in for DSL at my office location, but it will be 30 days before they install it.

So I need a method that will allow me to use both ISP's in the meantime.

I do appreciate the help.

CSSJR

---

