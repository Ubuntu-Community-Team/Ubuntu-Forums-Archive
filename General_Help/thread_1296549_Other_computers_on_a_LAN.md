---
title: "Other computers on a LAN"
date: 2009-10-20
forum: General Help
---

### Post by Snow986 on 2009-10-20
Hi All,

   I am just curious if there is a command that will allow me to see the other computers on my LAN and their IP's.  I've been researching this and I haven't been able to figure out if it is possible.

Thanks.

---

### Post by hurdevan on 2009-10-20
I don't think there is just a command that will do the trick but... Your router will tell if you can login to it.

---

### Post by undecim on 2009-10-20
"avahi-browse --all" will show a list of all services broadcast on the network.

If it is YOUR network, you can try using nmap to ping scan. install nmap and run "nmap -sP 192.168.1.0/24" replacing 192.168.1.0/24 with your network subnet (only try this on YOUR network. You can get in trouble doing this on someone elses)

Of course, if its your network, your router can give you most of these addresss (with the DHCP clients list). The only exception being those that use static IP addresses.

---

### Post by Snow986 on 2009-10-28
No luck with these and its not my network so I don't want to do anything that will get me into trouble.  Thanks for trying.  Any other ideas?

---

### Post by Giblet5 on 2009-10-28
The only "safe" thing you can do is look at NFS servers or windows shares.

Click Places -> Network

and browse.

Anything else, like ping scanners or port scanners will immediately raise the attention of your IT staff.

---

### Post by CrusaderAD on 2009-10-28
> **undecim said:**
> "avahi-browse --all" will show a list of all services broadcast on the network.

If it is YOUR network, you can try using nmap to ping scan. install nmap and run "nmap -sP 192.168.1.0/24" replacing 192.168.1.0/24 with your network subnet (only try this on YOUR network. You can get in trouble doing this on someone elses)

Of course, if its your network, your router can give you most of these addresss (with the DHCP clients list). The only exception being those that use static IP addresses.

Sweet, thanks for the info!

---

