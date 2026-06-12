---
title: "MySQL failing to start"
date: 2011-08-18
forum: General Help
---

### Post by Colin@oxford on 2011-08-18
Earlier today (a previous boot) MySQL was working fine.  Now it keeps failing and restarting. The mysql log says:
```

110818 12:43:02 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
110818 12:43:02 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110818 12:43:02  InnoDB: Started; log sequence number 0 44463
110818 12:43:02 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist

```

repeatedly...

Can anyone suggest the reason for this and a way of fixing it?
I tried running mysql_upgrade, but that requires a working MySQL :-(

---

### Post by Habitual on 2011-08-18
output suggests "Please run mysql_upgrade to create it."...?

---

### Post by Colin@oxford on 2011-08-18
> 
output suggests "Please run mysql_upgrade to create it."...?


As I said..
> 
I tried running mysql_upgrade, but that requires a working MySQL 


It all worked this morning and I haven't consciously changed anything

---

### Post by Habitual on 2011-08-18
yeah, my bad, anyway...

You could try 
```
sudo dpkg-reconfigure mysql-server-5.1
```

your installed mysql-server-xx version may be different.

---

### Post by raja.genupula on 2011-08-18
> **Habitual said:**
> yeah, my bad, anyway...

You could try 
```
sudo dpkg-reconfigure mysql-server-5.1
```

your installed mysql-server-xx version may be different.

hey , i have a doubt 
what the operation going to done if i give the command with any application , was it report the errors or making corrections automatically to the broken thing . if corrections done to broken thing what about settings have configured to that application . are they lost ?

& one more thing what can i expect from this 


```
sudo dpkg --configure <application>
```

---

