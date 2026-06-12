---
title: "Mysql my.cnf IPs"
date: 2011-07-07
forum: General Help
---

### Post by BattousaiX on 2011-07-07
I'm making an app to record sound and send the files back to my PC via FTP and make database updates describing what was sent as a project a few friends and I are working on.  I know it's small to begin with, but; I may deploy a larger app in the future that may require numerous users access to my database.  I was curious if there's a way to not require each IP to be added to my.cnf.

Details can be found here.  [http://ubuntuforums.org/showthread.php?p=11020148#post11020148](http://ubuntuforums.org/showthread.php?p=11020148#post11020148)

---

### Post by Habitual on 2011-07-07
MySQL permissions are NOT determined by the contents of my.cnf

```
GRANT priv TO user ON db.* TO db_user@'remote_host' IDENTIFIED BY 'db_pass'
```

remote_host is usually IP or '%' (wildcard = any host)
and the guest "user" would connect as 
```
mysql -h ipa.ddr.ess -udb_user -p
```
ipa.ddr.ess being your mysql server IP address.

[Adding Users to MySQL](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

---

### Post by BattousaiX on 2011-07-07
I'm not sure if what I stated made sense. I'm familiar with granting.  Please follow this thread.  I was being denied by the server before making changes to my.cnf.

[http://ubuntuforums.org/showthread.php?p=11020407#post11020407](http://ubuntuforums.org/showthread.php?p=11020407#post11020407)

view post #9 for full details.

---

### Post by Habitual on 2011-07-08
no thanks.
I work hard enough without having to 'double-back' to another thread.

I'm no java guru but I'd say that a failure to connect to MySQL using java should NOT throw "Exception in thread 'main'" errors. My guess is that java is the issue, not MySQL.

You increase your chances of a successful solution by sticking to one thread per issue.

good luck.

---

