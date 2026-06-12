---
title: "Prep server for SSL connections"
date: 2011-03-31
forum: General Help
---

### Post by ondemanddesign on 2011-03-31
So it seems that by default Ubuntu does not have port 443 open to access. Why is this and how do I open it?

```
netstat -tulpn
```
presents: (note: {myIP} is my servers IP masked)
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:135             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:33577           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:36714           0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:40333           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:53310           0.0.0.0:*               LISTEN      -
tcp6       0      0 :::22                   :::*                    LISTEN      -
udp        0      0 0.0.0.0:135             0.0.0.0:*                           -
udp        0      0 {myIP}:137       0.0.0.0:*                           -
udp        0      0 {myIP}:137       0.0.0.0:*                           -
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -
udp        0      0 {myIP}:138       0.0.0.0:*                           -
udp        0      0 {myIP}:138       0.0.0.0:*                           -
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -

```

Running the command 
```
iptables -A INPUT -i eth0 -p tcp --sport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
```
 had no changes to netstat.

---

### Post by falko on 2011-03-31
Run
```
a2enmod ssl
``` and restart Apache:
```
/etc/init.d/apache2 restart
```

Apache should now be listening on port 443 (HTTPS):

```
netstat -tap | grep https
```

---

