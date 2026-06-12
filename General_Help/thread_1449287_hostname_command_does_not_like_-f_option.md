---
title: "hostname command does not like -f option"
date: 2010-04-07
forum: General Help
---

### Post by Skaperen on 2010-04-07
The -f option is documented in the man page, and is a common option on other systems.  But it isn't working Ubuntu 9.10:```
altair/root /root 812# hostname -f
hostname: Unknown host
altair/root /root 813# which hostname
/bin/hostname
altair/root /root 814# /bin/hostname -f
hostname: Unknown host
altair/root /root 815# /bin/hostname --fqdn
hostname: Unknown host
altair/root /root 816# /bin/hostname --long
hostname: Unknown host
altair/root /root 817#
```This isn't the first thing where documentation doesn't match up with the commands. It works without the -f option. That section of the man page has:```
       -f, --fqdn, --long
              Display  the  FQDN (Fully Qualified Domain Name). A FQDN consists of a short host name and the DNS domain name. Unless you are using bind or NIS for host lookups you can change the FQDN and the DNS domain name (which is
              part of the FQDN) in the /etc/hosts file.
```

---

### Post by cjhabs on 2010-04-07
It works under 9.10 for me - I suspect you may have something wrong in your hosts file or in resolv.conf or in nsswitch.conf

---

