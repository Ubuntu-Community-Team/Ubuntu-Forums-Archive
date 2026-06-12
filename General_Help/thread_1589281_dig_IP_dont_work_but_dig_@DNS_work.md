---
title: "dig IP dont work but dig @DNS work"
date: 2010-10-06
forum: General Help
---

### Post by issamneo on 2010-10-06
hi all,
this is my nsswitch.conf:

```
passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
```

and this my resolv.conf:

```
nameserver myDNS_IP
```

the problem is when i type:
```
dig My_destination_host_ip
```
 
it tell's me:
;; connection timed out; no servers could be reached

but when i type:
```
dig @myDNS_IP My_destination_host_ip
```

it shows me the result and everything is OK???
do you know why when i type: dig My_destination_host_ip , it says no servers could be reached. As I know it have to check nsswitch.conf which tell's him to check /etc/hosts then the dns server which is myDNS_IP, so why !!!!

Thanks for your help

---

