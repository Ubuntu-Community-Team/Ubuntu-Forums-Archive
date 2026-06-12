---
title: "Error network configurations"
date: 2009-11-07
forum: General Help
---

### Post by fifoKamb3 on 2009-11-07
I was learning this tutorial:
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html)

But when I try to restart the network I get this:

> 
.....
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
...

Thanks

---

### Post by mbeach on 2009-11-07
What are you attempting to do?
What version of Ubuntu are you using? 
Can you provide a bit more background?
Can you post the contents of /etc/network/interfaces

---

### Post by Iowan on 2009-11-07
What did you change?
WHAT DID YOU DO????????????
(Just kidding...)
Might be as simple as a typo, */etc/network/interfaces* should help.

---

### Post by fifoKamb3 on 2009-11-07
mbeach, Iowan
Thank u both for ur appreciated replies.
I replaced **eth0 **by **eth3** in (* /etc/network/interface*) and it works now
I really don't know why I did that or what that means :-D, but when I looked in the results of *ifconfig * after doing the command *dhclient*, I saw somewhere there **eth3**.

I still can't find other machines in my home network using **ping **!!
I added my machines in */etc/hosts* but this is not the good solution I think.

I have an XP machine and I can (using ping) find the ubuntu work stations and server, but vice versa doesn't seem te work.

---

### Post by mbeach on 2009-11-08
can you ping those other computers by ip address or just not by their hostname?

from memory (and this may no longer apply), some solutions involve:
installing winbind (sudo apt-get install winbind)
ensuring your own hostname is being reported to some routers by ensuring /etc/dhcp3/dhclient.conf has a line like 
```
send host-name "<hostname>";
```
And something which I don't think is necessary anymore (but could be wrong), editing the hosts parameter somehow in the /etc/nsswitch.conf (be careful in there though), to include "wins" but only after you had installed winbind.

---

### Post by Iowan on 2009-11-08
Glad you found a solution - hope it keeps working. I've seen some threads where eth# kept climbing. 

**ping** by name or address? You can add the *other* machines to your */etc/hosts* file, but that doesn't work well if they get DHCP address. Otherwise, you may need a local DNS server. Some routers apparently have **dnsmasq** for their DHCP/DNS server (which ties the two together).

---

### Post by fifoKamb3 on 2009-11-09
> **mbeach said:**
> can you ping those other computers by ip address or just not by their hostname?
Yes.

I have these machines:
server1 (ubuntu server 7.10) with ip 192.168.1.2
wsubuntu (ubuntu 9.10 desktop edition) with dynamic ip.

I use wsubuntu and when I **ping server1** I can find it, and **ping 192.168.1.2** works as well. If I use server1 I can't ping wsubuntu (but ping [ip of wsubuntu] works) and I can't even find server1 on server1 with **ping server1** :)

Thanks

---

### Post by fifoKamb3 on 2009-11-09
> **Iowan said:**
> Glad you found a solution - hope it keeps working. I've seen some threads where eth# kept climbing. 
It keeps working but what is that eth0, eth1, eht3 ..?
my desktop edition ubuntu 9.10 works with eth0
but it gets an ip dynamically.

> **ping** by name or address? You can add the *other* machines to your */etc/hosts* file, but that doesn't work well if they get DHCP address. 
/etc/hosts works if all my machines have static ip :p

> Otherwise, you may need a local DNS server. Some routers apparently have **dnsmasq** for their DHCP/DNS server (which ties the two together).
how can I know if this dns server is installed or not?

---

