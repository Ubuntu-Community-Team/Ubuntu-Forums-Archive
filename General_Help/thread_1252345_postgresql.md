---
title: "postgresql"
date: 2009-08-28
forum: General Help
---

### Post by johnh10000 on 2009-08-28
Hi I have installed campcaster, and postgresql.  It's unlikly I'll be using postgres, for anything else.  I would be greatul if one of you could help me resolve the following:


*************************
* StorageServer Install *
*************************
DB Error: connect failed
 [nativecode=pg_pconnect(): Unable to connect to PostgreSQL server: FATAL:  no pg_hba.conf entry for host "::1", user "campcaster", database "Campcaster", SSL off] ** pgsql(pgsql)://campcaster:PASSWORD@localhost/Campcaster
Database connection problem.
Check if database 'Campcaster' exists with corresponding permissions.
dpkg: error processing campcaster-station (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of campcaster-studio:
 campcaster-studio depends on campcaster-station (= 1.4.0-3beta3); however:
  Package campcaster-station is not configured yet.
dpkg: error processing campcaster-studio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 campcaster-station
 campcaster-studio

---

### Post by peeyush2005 on 2009-09-18
I am getting the same problem...  please help !!

---

### Post by westbywest on 2009-10-20
The problem here appears to be with the format of some lines in the Postgresql file /etc/postgresql/8.3/main/pg_hba.conf, using IPv4 syntax when Campcaster is trying to connect via IPv6.

I fixed this by changing this line in pg_hba.conf:

```
host    all         all         127.0.0.1    255.255.255.255   password
```

with these two lines (accept both IPv4 and IPv6 connections):

```
host    all         all         127.0.0.1/32   password
host    all         all         ::1/128   password
```

Restarted postgresql, and then campcaster worked.

---

### Post by johnh10000 on 2009-10-20
> **westbywest said:**
> The problem here appears to be with the format of some lines in the Postgresql file /etc/postgresql/8.3/main/pg_hba.conf, using IPv4 syntax when Campcaster is trying to connect via IPv6.

I fixed this by changing this line in pg_hba.conf:

```
host    all         all         127.0.0.1    255.255.255.255   password
```

with these two lines (accept both IPv4 and IPv6 connections):

```
host    all         all         127.0.0.1/32   password
host    all         all         ::1/128   password
```

Restarted postgresql, and then campcaster worked.

Thanks, not near the box, at the mo.  will let u know

---

