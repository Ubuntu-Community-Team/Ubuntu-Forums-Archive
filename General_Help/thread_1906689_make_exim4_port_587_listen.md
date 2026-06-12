---
title: "make exim4 port 587 listen"
date: 2012-01-09
forum: General Help
---

### Post by igmox on 2012-01-09
hi,

i am trying to setup a relay smtp server and i cant make exim4 listen to port 587.

any help appreciated
thanks

---

### Post by CapnKirk on 2012-01-10
On my gentoo box with exim 4.77 I have this in /etc/exim/exim.conf:
```
daemon_smtp_ports = 25 : 465 : 587
```
This causes exim to listen at ports 25, 465 and 587. After changing the conf file, restart exim. Should be just that simple.

To check that exim is listening on the correct ports, as root do:
```
netstat -l --numeric-ports
``` or
```
sudo netstat -l --numeric-ports
```

HTH,
Kirk

---

### Post by igmox on 2012-01-10
must be different in ubuntu.
there is no /etc/exim/exim.conf

---

### Post by CapnKirk on 2012-01-10
Yes, sorry. Ubuntu does things "The Debian Way." See [**the Ubuntu docs on exim4**]("https://help.ubuntu.com/8.04/serverguide/C/exim4.html") for the details are where config data is stored.

You probably will find the place in /etc/exim4. You can quickly find what the current port configuration is by doing
```
grep -R daemon_smtp_ports *
```
That should tell you which file to edit.

Kirk

---

### Post by CapnKirk on 2012-01-11
Oh, and let us know how it went, and what solved your problem. It's nice to know if something worked and it's good for others later who have the same question/problem.

Thanks.

Kirk

---

