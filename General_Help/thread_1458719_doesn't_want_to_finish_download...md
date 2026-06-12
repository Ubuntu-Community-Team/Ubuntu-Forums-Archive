---
title: "doesn't want to finish download.."
date: 2010-04-20
forum: General Help
---

### Post by Spikerok on 2010-04-20
try to download mysql-server
[PHP]
apt-get install mysql-server
[/PHP]
but it seem to stop downloading this package at 5%

Tried converting rpm to deb with alens still no luck..
[PHP]
alien -i --scripts  MySQL-server-5.1.45-1.glibc23.x86_64.rpm
error: incorrect format: unknown tag
chown: cannot access `MySQL-server-5.1.45//etc/my.cnf': No such file or directory
failed chowning /etc/my.cnf to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 3.
[/PHP]

---

### Post by colorlessprism on 2010-04-20
i am not familiar with this error, but when i run into software sources issues i change my download server. if you pull up "software sources" under the administration category, and got to the "ubuntu software" tab you should see a drop down for "download from" and change it to a different server. ive run into this twice, but then again i also went through a sort of optimization where ubuntu picked the fastest server for me.

---

### Post by Spikerok on 2010-04-20
no, tried that.

---

### Post by Spikerok on 2010-04-20
adding next line to /etc/apt/sources.list 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main 

Didn't help

---

### Post by Spikerok on 2010-04-21
bump.

---

