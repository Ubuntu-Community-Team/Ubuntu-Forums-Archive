---
title: "Pure-ftpd (Virtual Users) problem"
date: 2011-05-21
forum: General Help
---

### Post by PGZ09 on 2011-05-21
Hello,

I am trying to get running pure-ftpd (using puredb, virtual users) but I am not being able to login.

I am afraid it is not getting the correct information from the puredb...

Here is how I have set it up:

```
apt-get install pure-ftpd-common pure-ftpd
useradd -g www-data -d /dev/null -s /bin/false ftpuser
cd /etc/pure-ftpd/conf
echo yes > ChrootEveryone
echo no > PAMAuthentication
echo no > UnixAuthentication
cd ../auth
ln -s ../conf/PureDB 50pure
pure-pw useradd teste -u ftpuser -d /var/www/teste
pure-pw mkdb
service pure-ftpd restart
```

Any help please?

Thanks.

---

