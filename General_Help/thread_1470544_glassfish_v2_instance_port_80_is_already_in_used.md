---
title: "glassfish v2 instance port 80 is already in used?"
date: 2010-05-02
forum: General Help
---

### Post by tee4cute on 2010-05-02
This is my netstat output :

netstat -aen --tcp

Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      0          5292
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      0          5290
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      0          20019
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          73928
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      0          436740
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      0          185452
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      0          5291
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      0          5293
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      117        14508
tcp        0      0 192.168.0.111:22        183.89.76.33:3695       ESTABLISHED 0          545638
tcp6       0      0 :::5900                 :::*                    LISTEN      1000       472652
tcp6       0      0 :::21                   :::*                    LISTEN      0          20021
tcp6       0      0 :::22                   :::*                    LISTEN      0          73930
tcp6       0      0 ::1:631                 :::*                    LISTEN      0          436739
tcp6       0    184 192.168.0.111:5900      183.89.76.33:3666       ESTABLISHED 1000       544417

As the output described, there is no listening port on 80 or 81.
But when I try to create glassfish v2 domain using command :

asadmin create-domain --user ..... --instanceport 80 domain1

I've got this error

Port 80 is already in used.

I tried for port 81 and the result is the same.

Firstly, I think that this may be glassfish issues but when I try to create domain with default port (8080), everything is OK!

So, I don't know why glassfish says that the port 80, 81 are already in used?

Thanks.

---

### Post by tee4cute on 2010-05-03
Anybody help me please???

T^T

---

### Post by natescott on 2010-05-13
Linux doesn't let you run apps listening on ports <1024 anymore without superuser privileges. There are a few ways to  get around this. I have a few prod servers using iptables to forward 80 to 8080. Once set up I have no trouble. You can search the internet on this and other ways to workaround this limitation.

---

