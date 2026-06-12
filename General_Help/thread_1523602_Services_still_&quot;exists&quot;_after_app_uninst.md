---
title: "Services still &quot;exists&quot; after app uninstall?"
date: 2010-07-03
forum: General Help
---

### Post by revered on 2010-07-03
When I am in a terminal and I do "service [press TAB key]" and get the list of services I see several services from apps I've removed (mostly using apt-get remove, and then purge autoremove and autoclean).  For example I see, guarddog and firestarter, I uninstalled them both but I see the services in the list, if I try to use them it says "unrecognized service".  How do I remove them from that list?  Im using ubuntu 10.04 lts

---

### Post by lsmobrian on 2010-07-03
read through the manpage for update-rc.d, I think this is probably what you want

```
update-rc.d guarddog remove
```

if it fails, then /etc/init.d/guarddog probably still exists, delete that file and re-run update-rc.d

---

### Post by revered on 2010-07-04
Thanks.  ps. tried to edit but can't find where to set it as solved.

---

