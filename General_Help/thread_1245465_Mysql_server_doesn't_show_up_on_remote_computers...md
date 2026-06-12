---
title: "Mysql server doesn't show up on remote computers.."
date: 2009-08-20
forum: General Help
---

### Post by shredder12 on 2009-08-20
I have installed the mysql server and when I tried to connect it from a  PC on lan, I was unable to connect. Scanning through Nmap showed that mysql service was turned off even though it was working.

Some help plz..

---

### Post by Bachstelze on 2009-08-20
Please paste the output of

```
sudo netstat -aln | grep LISTEN
```

---

### Post by DaithiF on 2009-08-20
Hi,
by default a new mysql install isn't accessible from external machines, only locally.

to enable access from the network, find and comment out (prepend a # character) to the line:
bind-address 127.0.0.1
in the conf file /etc/mysql/my.cnf
then restart mysqld
sudo /etc/init.d/mysql restart

---

### Post by shredder12 on 2009-08-20
> **DaithiF said:**
> Hi,
by default a new mysql install isn't accessible from external machines, only locally.

to enable access from the network, find and comment out (prepend a # character) to the line:
bind-address 127.0.0.1
in the conf file /etc/mysql/my.cnf
then restart mysqld
sudo /etc/init.d/mysql restart

hey, thanks it worked..

---

