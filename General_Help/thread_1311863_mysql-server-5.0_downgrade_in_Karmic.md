---
title: "mysql-server-5.0 downgrade in Karmic?"
date: 2009-11-02
forum: General Help
---

### Post by dexterchief on 2009-11-02
I just set up a VM for my rails dev work and it was all running nicely using mysql 5.1. When I realized that I need to do some work on an older app (rails 2.1) I tried to downgrade to mysql 5.0 but got the following error:

mike@railsdev:~$ sudo aptitude install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  mysql-server-5.0 
0 packages upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/23.8MB of archives. After unpacking 79.7MB will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 150337 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb) ...
[B]Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/B]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

I did purge the mysql 5.1 packages out before trying to install.
I have tried adding the repos for jaunty and installing from there but I get the same error. Any ideas on how to fix this and get 5.0 running in karmic?

---

### Post by dexterchief on 2009-11-02
Looks like I solved my own problem. As it happens you can solve this by renaming/removing the /var/lib/mysql/debian-*.flag

Strange but true.

---

### Post by erderr on 2009-12-19
Sweet... that helped me to, as I'm trying to setup a trail mysql cluster :>

Saves me having to use my brain :D lol

Thanks!

---

### Post by dukla on 2010-01-09
What are exact commands to downgrade please? One by one please ...  to have this version function with php and apatche which are already installed with mysql 5.1?

Also after install 5.0 and using apt-get update/upgrade will "it want" to install 5.1 or not?

And during downgrade process will I lose any mysql data? like tables and data etc? Thx

---

### Post by dukla on 2010-01-09
Again nobody knows ....

---

### Post by dexterchief on 2010-02-03
Hey dukla,
you can use synaptic and use force version under the package menu.
I don't think it will delete your data (I don't think it did with mine), but I would do a mysqldump first just to be safe.
I hope that helps even if it is a few weeks to late. :)

---

### Post by mattack on 2010-03-09
> **dexterchief said:**
> Looks like I solved my own problem. As it happens you can solve this by renaming/removing the /var/lib/mysql/debian-*.flag

OMG! Thanks for this! I too tried to downgrade mysql and got the same error... Whew.

---

