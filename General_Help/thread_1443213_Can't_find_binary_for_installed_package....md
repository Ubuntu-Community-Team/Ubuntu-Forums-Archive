---
title: "Can't find binary for installed package..."
date: 2010-03-30
forum: General Help
---

### Post by lanza23 on 2010-03-30
On a Linode (Ubuntu 9.10 Karmic Koala), I tried to install php-config, which seems to work, but I can't find it (I had no problems installing/finding it on my home system, also Ubuntu 9.10)...

root@localhost:~# apt-get install php-config
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
php-xml-parser
The following NEW packages will be installed:
php-config
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 0B/34.2kB of archives.
After this operation, 340kB of additional disk space will be used.
Selecting previously deselected package php-config.
(Reading database ... 20454 files and directories currently installed.)
Unpacking php-config (from .../php-config_1.10.11-1_all.deb) ...
Setting up php-config (1.10.11-1) ...

Then...

root@localhost:~# dpkg -l | grep php-config
ii php-config 1.10.11-1 Your configuration's swiss-army knife
root@localhost:~# ls /usr/bin/ | grep php-config
root@localhost:~# ls /usr/sbin/ | grep php-config
root@localhost:~# ls /usr/local/bin/ | grep php-config
root@localhost:~# ls /usr/local/sbin/ | grep php-config
root@localhost:~# which php-config
root@localhost:~# whereis php-config
php-config:

---

### Post by lanza23 on 2010-03-30
It's a shell script, not a binary...maybe I'll just copy the one from my home system...

---

### Post by lanza23 on 2010-03-30
I needed to "apt-get install php5-dev"...then php-config appeared in /usr/bin

---

