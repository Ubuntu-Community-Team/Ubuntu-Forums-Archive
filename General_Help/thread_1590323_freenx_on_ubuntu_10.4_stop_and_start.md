---
title: "freenx on ubuntu 10.4 stop and start"
date: 2010-10-07
forum: General Help
---

### Post by DerDen on 2010-10-07
I Installed freenx server on my Ubuntu 10.4 Lucid (32 bit) installation, exactly as described here:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

after that: the software is working fine...

now I want to be able to start / stop freenx, so as decribed on the same link i give:
sudo /etc/init.d/freenx-server stop

then I get the following message:
"
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service freenx-server stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop freenx-server
"

after that I am still able to login with an nx session..

so i try the two advices i got after the first attempt:
service freenx-server stop
---response: stop: Unknown job: freenx-server
stop freenx-server
---response: stop: Unknown job: freenx-server

so as you can expect: I can still logon with my nomachine client to freenx-server

what am I doing wrong... what is the correct command to stop and start freenx?

---

### Post by DerDen on 2010-10-09
bump

---

### Post by DerDen on 2010-10-12
still no answer...is the question that difficult, or that stupid?

---

### Post by popebrak on 2010-10-14
I having precisely the same problem.

pope@plato:~$ sudo start freenx-server
start: Unknown job: freenx-server
pope@plato:~$ sudo initctl list|grep freenx
pope@plato:~$ 

I downloaded and ran the extra install script mentioned on the ubuntu documentation wiki, but it doesn't look like it created an upstart job.

---

### Post by meklinux on 2010-12-13
Well, I have the same problem. No answers for us?


maybe it helps for you, anyway, look for the binary nxserver. I found it here: /usr/bin/nxserver
then just do a: /usr/bin/nxserver start

Afterall freenx is running on the server, but i still cant connect from the client - well this is another problem.

---

### Post by hantms on 2011-01-09
Bump.. having the same issue.

---

### Post by johanneslandin on 2011-01-23
This worked for me:
$ sudo /usr/bin/nxserver --stop
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 123 Service stopped
NX> 999 Bye

$ sudo /usr/bin/nxserver --start
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 122 Service started
NX> 999 Bye

---

