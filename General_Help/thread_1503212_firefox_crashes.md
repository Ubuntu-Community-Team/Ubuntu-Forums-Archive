---
title: "firefox crashes"
date: 2010-06-06
forum: General Help
---

### Post by luckylucky on 2010-06-06
firefox has been crashing a lot.

Apparently (from googling) this is an Ubuntu kernel problem, not firefox's fault.

The solution is apparently this:

sudo add-apt-repository ppa:bryceharrington/purple && apt-get update && apt-get upgrade

but I get this problem

> 
$ sudo add-apt-repository ppa:bryceharrington/purple && apt-get update && apt-get upgrade
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 510DE9AC846B40EB94EDB3AEFBB49579B75FECB0
gpg: requesting key B75FECB0 from hkp server keyserver.ubuntu.com
gpg: key B75FECB0: "Launchpad PPA for Bryce Harrington" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory



How does one fix this?  Thanks

---

### Post by luckylucky on 2010-06-06
bump

---

### Post by sites on 2010-06-06
Can you post a link to this "solution", please?

---

### Post by luckylucky on 2010-06-06
Here is one such link
[http://www.neowin.net/news/ubuntu-1004-bug-causing-firefox-crashes](http://www.neowin.net/news/ubuntu-1004-bug-causing-firefox-crashes)
they are all pretty much saying the same thing

---

### Post by luckylucky on 2010-06-07
bump

---

### Post by luckylucky on 2010-06-08
Solved this myself

first for whatever bizzar reason you actually have to switch to root; sudo won't do

sudo su

then run

sudo add-apt-repository ppa:bryceharrington/purple && apt-get update && apt-get upgrade

(yes, with sudo)

---

