---
title: "Can't Access Mysql"
date: 2009-10-19
forum: General Help
---

### Post by josephmcnelis on 2009-10-19
Hey All,

Im still trying to set up my vps, got most of what i thought was the hard stuff out of the way now im stuck with a mysql problem.

When i try to log in as root, it says i access denied.

 I've tried everything i can think of, reconfiguring mysql via dpkg, using the the mysqld --skip-grant-tables command to get in.

I  done select * user; when i got access via the --skip-grant-tables command and it only returned the user debian-sys-maint. So i figured i would add the root user account but apparently i dont have permission to create when logged in as such.

Im tearing my hair out, everyone else with this problem seems to solve it very easily yet none of the solutions work for me.

Im running Ubuntu Hardy.

Any help would be greatly appreciated. :)

---

### Post by josephmcnelis on 2009-10-19
I think ive found away around it.

---

### Post by Ikka3990 on 2009-11-13
I am facing the same problem. Can you please explain the workaround you've mentioned above?

---

### Post by wojox on 2009-11-13
Log in as root on mysql:

```
mysql -u root -p <password you used when installing>
```

---

### Post by Jive Turkey on 2009-11-13
it could be a number of things but first you should look at your /etc/mysql/my.cnf file and make sure you dont have "skip-networking" there.  That will keep remote clients out.  I think you need to specify a listen address to enable it and then grant access to the user to access from other than localhost with an update query.

If you are ssh'ed to the vps already try updating the superuser password there.

---

