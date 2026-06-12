---
title: "Updates problem"
date: 2012-04-01
forum: General Help
---

### Post by SwaroopKunduru on 2012-04-01
W:Failed to fetch [http://archive.canonical.com/dists/Oneiric/partner/source/Sources](http://archive.canonical.com/dists/Oneiric/partner/source/Sources)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/Oneiric/partner/binary-i386/Packages](http://archive.canonical.com/dists/Oneiric/partner/binary-i386/Packages)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/Ocelot/partner/source/Sources](http://archive.canonical.com/dists/Ocelot/partner/source/Sources)  404  Not Found [IP: 91.189.92.191 80]

---

### Post by wildmanne39 on 2012-04-01
Hi, those ppa's are not on the sever or the server is down so you can remove them. Please do:
```
gksu software-properties-gtk
```
in a terminal, uncheck the appropriate boxes under the 'Other Software' tab. Close the program when you're done, and it should prompt you to reload the sources lists do that and it should work.
Thanks

---

### Post by SwaroopKunduru on 2012-04-01
I did exactly the same but I am not sure what to unselect. I unselected 4 which is giving problem when Installing Maven 3.

Please see the problem below.

installArchives() failed: Selecting previously deselected package maven3.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 218780 files and directories currently installed.)
Unpacking maven3 (from .../maven3_3.0.3-0~ppa1_all.deb) ...
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
Setting up maven3 (3.0.3-0~ppa1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 qmail
 qmail-run
Error in function: 
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured

Please see my command below:

swaroop@swaroop-s5710t:~$ hostname --fqdn
swaroop-s5710t

---

### Post by learner11 on 2012-06-12
I too have a similar problem :


 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am using Ubuntu 12.04. How to resolve this problem ?

---

### Post by huangpatrick on 2012-07-05
> **learner11 said:**
> I too have a similar problem :


 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am using Ubuntu 12.04. How to resolve this problem ?

you can solve the problem with set the /etc/hosts file,modify the line
"127.0.0.1 hostname "to "127.0.0.1 [www.yourdomain.com](www.yourdomain.com) hostname" ,make sure 
that "hostname --fqdn" echo the XXX.XXX type,not just a hostname like "ubuntu" .

---

