---
title: "problem in vnstat!!"
date: 2009-07-23
forum: General Help
---

### Post by harivittal.hk on 2009-07-23
hi! i am using vnstat to knw my b/w usage..but its not updating the database..this is the error tat i m gettin..
vnstat -u -i eth0
Error:
Unable to read database "/var/lib/vnstat/eth0".
Error:
Unable to write database "/var/lib/vnstat/eth0".
Make sure it's write enabled for this user.
Database not updated.

plz let me knw how to remove this bug...:(

---

### Post by sloggerkhan on 2009-07-23
When you first run vnstat it will create a database file. It is documented in the man page. Without a database file or proper permissions and configuration, vnstat will not function.

```

 vnstat  -u  -i interface forces a database update for interface or cre&#8208;
       ates the database if it doesn&#8217;t exist. This is usually the  first  com&#8208;
       mand used after a fresh install.

```

---

### Post by harivittal.hk on 2009-07-23
after i gave tat command this is what i got!!
vnstat -u -i
Error:
Interface for -i missing.

---

### Post by sloggerkhan on 2009-07-24
yeah, like eth0 or eth1 etc... whatever your card is at? ...

---

### Post by Vergo on 2009-07-25
First you'll need to find out what the name (or names) of your network interfaces are. Try something like
```
ifconfig | grep Ethernet
```
The first word on each line it outputs is the name of a network interface. For me (with two network cards) the output is
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
```
so the interface names in my case are eth0 and eth1. That's likely to be only eth0 or something different for you.

Next just introduce that interface you'd like to monitor to vnStat:
```
sudo vnstat -u -i eth0
```

That's the only time you need to use "sudo" when calling vnStat. After that, a simple "vnstat" will give you output after some time and traffic has passed. See "vnstat --help" for the other output options.

---

