---
title: "Ubuntu Server FQDN."
date: 2010-10-16
forum: General Help
---

### Post by melrokz on 2010-10-16
How to set the hostname and FQDN on Ubuntu Server 10.04?

---

### Post by CharlesA on 2010-10-16
You get the hostname by editing:

```
/etc/hostname
```

```
/etc/hosts
```

Not sure how you'd edit the DNS name tho.

---

### Post by melrokz on 2010-10-16
I'd like to have a link to the DNS configuration too.

---

### Post by CharlesA on 2010-10-16
It looks like you'd change the FQDN by editing the the part in blue in /etc/hosts:

```
127.0.0.1       localhost
192.168.1.34    [COLOR="Blue"]mars.asgard.lcl[/COLOR] mars

```

As for editing the which DNS servers are used for name resolution, they would be found in:

```
/etc/resolv.conf
```

---

### Post by btindie on 2010-10-16
```
man hosts
man hostname
```

/etc/hostname should only contain the hostname (i.e. server) and not the FQDN (i.e. server.domain). The domain is then set through DNS / /etc/hosts as mentioned above.

---

### Post by CharlesA on 2010-10-16
You also have to set the correct domain name in /etc/resolv.conf, so it'll know where to look.

---

