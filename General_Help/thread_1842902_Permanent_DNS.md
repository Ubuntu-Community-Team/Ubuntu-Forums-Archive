---
title: "Permanent DNS"
date: 2011-09-12
forum: General Help
---

### Post by Steam. on 2011-09-12
I want to setup a permanent DNS on ubuntu 10.04.I need the Google Public DNS to be set on it, so i gedit the resolv.conf file, save, then it works.Next reboot they return to the before google dns ones.How can I make this change permanent?

---

### Post by SeijiSensei on 2011-09-12
Edit (as root with sudo) /etc/dhcp3/dhclient.conf and change the commented-out "prepend" directive so it reads:

```
prepend domain-name-servers 8.8.8.8;
```

That will now be the first entry in /etc/resolv.conf.

---

### Post by Steam. on 2011-09-12
Thank you a lot.There is no router and I couldn't set the DNS from there so this was very helpful.Thanks again.

---

