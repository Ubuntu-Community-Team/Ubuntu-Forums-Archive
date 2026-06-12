---
title: "dpkg: error processing qmail (--configure):  subprocess installed post-installation s"
date: 2012-07-22
forum: General Help
---

### Post by marwa aly on 2012-07-22
i try to install program on ubuntu 12.04 and here are what were written on terminal:

The program 'show' is currently not installed.  You can install it by typing:

[email]root@drtamer-G41MT-S2PT:/home/marwa/arb.64.ubuntu[/email] # show help
The program 'show' is currently not installed.  You can install it by typing:
apt-get install nmh
[email]root@drtamer-G41MT-S2PT:/home/marwa/arb.64.ubuntu[/email] # apt-get install nmh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nmh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 332 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
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
 
so what can i do  and what these lines mean??????????????????:confused::confused::(

---

### Post by marwa aly on 2012-07-23
**t**[B]here are no body help me????????????????:confused::confused::confused: 
i need a help please[/B]:(:(

---

### Post by marwa aly on 2012-07-23
:(:(please i need helllllllllllllllllllllp:confused:

---

