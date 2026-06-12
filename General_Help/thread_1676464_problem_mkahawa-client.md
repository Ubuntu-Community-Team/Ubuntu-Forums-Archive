---
title: "problem mkahawa-client"
date: 2011-01-27
forum: General Help
---

### Post by mahsom on 2011-01-27
Hello .
I use ubuntu-10.10 .
receive this message after runing mkahawa-client :
```
root@Gclient:/home/station5# sh -x /etc/init.d/mkahawa-clientd start
+ PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
+ DAEMON=/usr/sbin/mkahawa-clientd
+ NAME=mkahawa-client
+ DESC=mkahawa-clientd
+ LABEL=Mkahawa Daemon
+ test -x /usr/sbin/mkahawa-clientd
+ LOGDIR=/var/log/mkahawa-client
+ PIDFILE=/var/run/mkahawa-client.pid
+ DODTIME=1
+ [ -f /etc/default/mkahawa-client ]
+ . /etc/default/mkahawa-client
+ USERNAME=station5
+ SERVER_ADDR=192.168.56.2
+ CLIENT_NAME=S5
+ SSL=no
+ set -e
+ echo -n Starting mkahawa-clientd: 
Starting mkahawa-clientd: + pidof -x /usr/sbin/mkahawa-clientd
+ [  ]
+ echo Starting mkahawa-client
Starting mkahawa-client
+ start-stop-daemon --start --quiet --pidfile /var/run/mkahawa-client.pid --exec /usr/sbin/mkahawa-clientd -- start
Initiated: start
Username: station5
No protocol specified
FXApp::openDisplay: unable to open display :0.0
No protocol specified
FXApp::openDisplay: unable to open display :0.0

```
mkahawa-client not start in ubuntu-10.10 .:(

---

### Post by mahsom on 2011-01-29
nobody help me ... !
what is this error ?
```
No protocol specified
FXApp::openDisplay: unable to open display :0.0

```

normal user can execute this script but on startup (runlevel2 ) not work !

---

### Post by nefrussy on 2011-12-30
First of all, sorry for my English is very bad.
Are you workin with normal pc or thin client (pxe)
if is with pxe you`ll have to boot from de bios and  set it to boot to the terminal lightly.
This will bring up the screen to enter the username and password.
To work with pre-light terminals will have to install and configure ltsp.

---

### Post by nefrussy on 2011-12-30
First of all, sorry for my English is very bad.
Moreover, from version 10.04 mkahawa have problems with updates. So far not even that.

---

