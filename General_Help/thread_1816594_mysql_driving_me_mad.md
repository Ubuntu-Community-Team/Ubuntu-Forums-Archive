---
title: "mysql driving me mad"
date: 2011-08-02
forum: General Help
---

### Post by JigglyWiggly_ on 2011-08-02
Ok so I want to use MYSQL administrator remotely, if I try I just get
Host 192.168.1.216 is not allowed to connect to this mysql server.


 All the fixes I see on the Internet are for specific databases, but I want to access everyhting? Why the hell is this so hard? It's giving me a bad headache.

---

### Post by JigglyWiggly_ on 2011-08-02
Nevermind, it's just much easier to just do it through a SSH tunnel
[http://www.vbmysql.com/articles/security/connecting-the-mysql-gui-tools-to-a-remote-server-through-a-firewall](http://www.vbmysql.com/articles/security/connecting-the-mysql-gui-tools-to-a-remote-server-through-a-firewall)

---

### Post by galvatron408 on 2011-08-02
if you still wanted to know... it's because mysql has permissions that you need to set. basically, your user is allowed localhost access but not from any other host.

Also, if you're having trouble with mysql, you should install phpmyadmin. It makes administering mysql easier.

---

### Post by blind2314 on 2011-08-02
> **galvatron408 said:**
> if you still wanted to know... it's because mysql has permissions that you need to set. basically, your user is allowed localhost access but not from any other host.
 
Also, if you're having trouble with mysql, you should install phpmyadmin. It makes administering mysql easier.
 
Unless you're in a production environment. In that case, please don't use phpmyadmin. Its security flaws are well documented.

---

### Post by galvatron408 on 2011-08-04
if you're concerned about security flaws, don't use Android, Windows, Sony, Macs, Linux or anything. They all have security flaws that are well documented.

---

### Post by bodhi.zazen on 2011-08-04
> **galvatron408 said:**
> if you're concerned about security flaws, don't use Android, Windows, Sony, Macs, Linux or anything. They all have security flaws that are well documented.

:lolflag:

---

