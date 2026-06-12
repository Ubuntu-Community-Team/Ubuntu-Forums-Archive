---
title: "upgrade to 10.04 broke DNS lookups in home subnet"
date: 2010-05-01
forum: General Help
---

### Post by meonkeys on 2010-05-01
I use the domain "myhome.local" in my house, and run a bind DNS server on Ubuntu so I can refer to machines by name.

After upgrading my server to Ubuntu 10.04, all DNS lookups in my ".local" domain fail. For example: "host box1.myhome.local" returns NXDOMAIN.

Does anyone know of changes in bind in 10.04 that I might need to account for?

---

