---
title: "chkconfig won't turn on dovecot"
date: 2010-11-15
forum: General Help
---

### Post by ksteuber on 2010-11-15
I want dovecot to start at boot and I can't seem to get this to work.

Initially, I installed chkconfig and tried to run "sudo chkconfig dovecot on". This generated a whole bunch of errors about upstart and insserv not getting along properly. I patched chkconfig according to a post on this page:
[https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/467000]("https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/467000")
This stopped the error messages, but hasn't solved my problem; now this happens:

```
ksteuber@nc-ubuntu-server:~$ sudo chkconfig dovecot on
ksteuber@nc-ubuntu-server:~$ chkconfig dovecot
dovecot  off
```

I thought maybe it was just chkconfig that wasn't working, but this works:

```
ksteuber@nc-ubuntu-server:~$ sudo chkconfig apache2 on
ksteuber@nc-ubuntu-server:~$ chkconfig apache2
apache2  on
ksteuber@nc-ubuntu-server:~$ sudo chkconfig apache2 off
ksteuber@nc-ubuntu-server:~$ chkconfig apache2
apache2  off
```

I also find it suspicious that the upstart patch is supposed to generate output, but chkconfig gives no output. I have tried redirecting stdout and stderr to a file, but it generates an empty file. 

I am running Ubuntu 10.10 64bit, kernel 2.6.35-22-server, dovecot 2.0.1

---

### Post by cariboo on 2010-11-15
Chkconfig, really shouldn't work anymore, as Ubuntu no longer uses init scripts. Ubuntu now uses [Upstart]("http://upstart.ubuntu.com/"). As far as I know there is an easy tool available  to create the scripts needed.

Have you tried using the following command:

```
sudo service dovecot start 
```

---

### Post by ksteuber on 2010-11-15
The command successfully starts dovecot, but does not start it at boot.

---

### Post by ksteuber on 2010-11-17
So do I need to use upstart to get dovecot to run at system boot? How do I do this?

---

### Post by ksteuber on 2010-11-17
Ok, I finally got it to work by adding this line to rc.local:
```
echo -n ' dovecot'; /usr/local/sbin/dovecot
```

---

### Post by k4nz4k1g4w4 on 2011-01-20
Thanks ksteuber

---

