---
title: "can connect to mysql after apt-get remove mysql*"
date: 2011-07-12
forum: General Help
---

### Post by bonfire89 on 2011-07-12
This thread is ultimately a complete waste, it was complete user error. Feel free to remove thread to keep clutter out of the forums.


Hello all, 

I'm using Ubuntu 11.04 Desktop and something very strange is happening with mysql. There is a lot to mention that is very bizarre but I believe this one thing describes the issue best

I ran

```
apt-get remove mysql*
```

yet I can still connect to the database with

```
mysql -u root -p
```

it seems as if there are two instances running or something.

If anyone could help me remove everything mysql related and just start fresh again it would be a big help.

Thanks!

---

### Post by uRock on 2011-07-12
Removing it via USC should remove everything. Removing it via Synaptic and selecting to completely remove, should also work.

---

### Post by bonfire89 on 2011-07-12
according to those two it isn't installed. :(

---

### Post by bonfire89 on 2011-07-12
I'm not sure what this means, but it might help 

```
dpkg --get-selections  | grep 'mysql'
libmysqlclient16				deinstall
mysql-common					deinstall
mysql-server-5.1				deinstall
php5-mysql					deinstall
```

---

### Post by uRock on 2011-07-12
Does running **sudo apt-get autoremove** in a terminal or does Synaptic offer any autoremovables after clicking on Status?

Uninstalling it via USC would have removed the dependancies, whereas apt-get remove and Synaptic will leave them.

---

### Post by bonfire89 on 2011-07-12
I just ran

```
apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ca-certificates-java dbconfig-common icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx java-common javascript-common libaccess-bridge-java libaccess-bridge-java-jni
  libdbi-perl libhtml-template-perl libjs-mootools libmcrypt4 libnet-daemon-perl libplrpc-perl openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib php5-gd php5-mcrypt
  ttf-dejavu-extra tzdata-java wwwconfig-common
```

which didn't list mysql, but, ran it anyway. No help.


The following may be of interest

```
whereis mysql
mysql: /etc/mysql
```

also

```
service mysql stop
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.265" (uid=1000 pid=12819 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))
```

---

### Post by bonfire89 on 2011-07-12
I hate to admit it, but I made a completely dumb move. I'm really sorry for wasting your time. I had two terminals open, one of which wasn't my local computer.

This is embarrassing. 

Thank you so much for your help though, again, I'm very sorry, a very dumb mistake.

---

### Post by uRock on 2011-07-12
No problem, it happens. :)

---

