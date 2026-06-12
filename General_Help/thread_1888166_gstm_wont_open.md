---
title: "gstm wont open"
date: 2011-11-28
forum: General Help
---

### Post by zpata on 2011-11-28
I'm trying to set up an ssh tunnel. Its my first time trying. I accidentally set up a tunnel that had the wrong info. Now when I try to open gstm  I get this: "Tunnel 'MyTunnel' stopped.  Warning: Identity file 187oaucc not accessible: No such file or directory. ssh: connect to host 127.0.0.1 port 22: Connection refused" and gtsm wont open to let me change it. Whatever shall I do?

---

### Post by lechien73 on 2011-11-28
Hi & welcome to the forums,

Firstly could you check if sshd is running by typing:

```
ps ax | grep sshd
```

On my system this produces:

```
1029 ?        Ss     0:00 /usr/sbin/sshd
```

If it is running, then check it it's listening on port 22:

```
netstat -ln | grep 22
```

---

### Post by zpata on 2011-11-29
its running and its listening

---

