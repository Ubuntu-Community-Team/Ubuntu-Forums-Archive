---
title: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysq"
date: 2010-04-16
forum: General Help
---

### Post by peterv6 on 2010-04-16
I'm running MySQL in Ubuntu 9.10. I installed MySQL this afternoon, and it worked just dandy. I logged off and shut down the laptop. When I got back on tonight, I get the following error when I run mysql:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

If I run mysqld, I get this message:

```
root@MBP17U<644>$: mysqld
100416 20:31:14 [Note] Plugin 'FEDERATED' is disabled.
100416 20:31:14  InnoDB: Started; log sequence number 0 44233
100416 20:31:14 [ERROR] Can't start server : Bind on unix socket: No such file or directory
100416 20:31:14 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
100416 20:31:14 [ERROR] Aborting

100416 20:31:14  InnoDB: Starting shutdown...
100416 20:31:15  InnoDB: Shutdown completed; log sequence number 0 44233
100416 20:31:15 [Warning] Forcing shutdown of 1 plugins
100416 20:31:15 [Note] mysqld: Shutdown complete


Fri Apr 16 20:27:28 EDT 2010
``` 

I'm quite new to this, so any and all comments are welcome.  I have no idea what FEDERATED is, or how to install it, and I have no idea how to check if another mysqld server is running.  Please help!

---

