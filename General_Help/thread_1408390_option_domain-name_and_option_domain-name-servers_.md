---
title: "option domain-name and option domain-name-servers lines required in dhcpd.conf?"
date: 2010-02-16
forum: General Help
---

### Post by intermentals on 2010-02-16
Ubuntu Server 9.10

I want to set up my dhcp server to also be my DNS server so do I skip these lines or point them at the same server that the config file is on?

Thanks

---

### Post by iponeverything on 2010-02-16
you need to hand out the nameserver address, the clients will not figure it out on their own.

---

### Post by intermentals on 2010-02-16
thanks but can it be the same server as dhcp is set up on?

---

### Post by iponeverything on 2010-02-17
yes it can give out its own address.

---

### Post by intermentals on 2010-02-17
ok thank you very much

---

