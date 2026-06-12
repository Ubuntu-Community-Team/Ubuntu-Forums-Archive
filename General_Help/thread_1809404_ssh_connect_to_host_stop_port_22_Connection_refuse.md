---
title: "ssh: connect to host stop port 22: Connection refused"
date: 2011-07-21
forum: General Help
---

### Post by neridaj on 2011-07-21
Hello,

I'm having problems with ssh and don't know what else to do. I keep getting "ssh: connect to host stop port 22: Connection refused" when i try to stop or start ssh:

sudo /usr/sbin/sshd -Dd
debug1: sshd version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-Dd'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Bind to port 22 on 0.0.0.0 failed: Address already in use.
debug1: Bind to port 22 on ::.
Bind to port 22 on :: failed: Address already in use.
Cannot bind any address.

sudo netstat -pantu | grep LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3948/sshd
sudo kill 3948

ssh stop
ssh: connect to host stop port 22: Connection refused

ssh start
ssh: connect to host start port 22: Connection refused

ssh localhost
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-10-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Thu Jul 21 11:42:06 2011 from localhost

SSH_AUTH_SOCK=0 ssh -T [email]git@github.com[/email]
Permission denied (publickey).

Thanks for any help.

---

### Post by mikejonesey on 2011-07-21
```
sudo lsof -i :22
```

---

### Post by The Cog on 2011-07-21
I think you are having two different probems here. 

Firstly, **sudo /usr/sbin/sshd -Dd** gives **failed: Address already in use.** This is because the sshd server is already running. But I think you figured that one out.

Secondly, the command **ssh stop** is a command to make an ssh connection to a host called stop. Similarly "ssh start" tries to connect to server called start. I think you want > sudo stop ssh or on older versions of Ubuntu you might need > sudo /etc/init.d/sshd stop

---

