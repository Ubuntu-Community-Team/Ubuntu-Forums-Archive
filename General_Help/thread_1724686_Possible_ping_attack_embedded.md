---
title: "Possible ping attack embedded?"
date: 2011-04-08
forum: General Help
---

### Post by nhanquy on 2011-04-08
When I do a "ping xxxx" which  xxxx is my NAS I got responses from an unfortunate 208.x.x.x in Boston!

Of course, 208.x.x.x is not my NAS at all. So with further investigation, it looks like if xxxx is unresolved, ping would go to that 208.x.x.x.

So why is that?  Did someone plant something in my Ubuntu machine to make it behave that way for his ping attack?

TIA

---

### Post by tredegar on 2011-04-08
We can't really help you if you just post "xxxx".

Is "xxxx" a domain name or an IP address?

I doubt your linux machine is compromised, and posting details of your LAN IPs or server names is most unlikely to expose you to additional threats.

Please provide some more information.

---

### Post by nhanquy on 2011-04-08
XXXX is a name of my NAS box (/etc/hosts). Actually it is TTNAS.

**_/etc/host:_**

> 127.0.0.1 localhost.localdomain localhost
192.168.1.9 TTNASso I can use TTNAS in _**/etc/fstab**_ for automount (on other machines)

> //TTNAS/Volume_1                   /mnt/xxx  ....
instead of 

> //192.168.1.9/Volume_1         /mnt/xxx ...


---

