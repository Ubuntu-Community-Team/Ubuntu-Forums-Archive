---
title: "Where does dhcp3 store it's leases"
date: 2006-03-20
forum: General Help
---

### Post by choizy on 2006-03-20
Well title says its all. I wanna know how manny ip's that is in use. and how manny is free. But where are the leases stored?

---

### Post by mr.p on 2006-03-20
[QUOTE=choizy]Well title says its all. I wanna know how manny ip's that is in use. and how manny is free. But where are the leases stored?[/QUOTE]
Off the top of my head, check in /var/cache/dhcp.., something around there usually.

---

### Post by choizy on 2006-03-20
Didn't find it :p

---

### Post by mr.p on 2006-03-20
[QUOTE=choizy]Didn't find it :p[/QUOTE]
Ok hrmmm... Run "sudo updatedb" and then do "locate leases" or "locate dhcp" see if you can find it that way.

---

### Post by mr.p on 2006-03-20
Have a look in /var/lib/dhcp/dhcpd.leases :)

---

