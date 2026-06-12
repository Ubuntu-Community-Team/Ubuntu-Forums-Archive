---
title: "Run TrueCrypt under regular user - still asks for password for the first time"
date: 2011-07-11
forum: General Help
---

### Post by dojigiri on 2011-07-11
I have problems running Truecrypt on Ubuntu for normal user. 
OS: Ubuntu Server 64-bit 10.04.2 LTS, minimal installation + GUI installed 
Truecrypt v.7.0a (standard, 64-bit), installed the standard way in the gui. 
 
In order to run TC under normal account, I created group "truecrypt" 
(groupadd truecrypt) 
and added my user to it 
(usermod -a -G truecrypt dojigiri) 
 
Modified the /etc/sudoers file, added: 
 
# Users in the truecrypt group are allowed to run truecrypt as root. 
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt --core-service 
 
(also tried without "--core-service") 
 
The problem is, that the first time I try to mount truecrypt volume, it  is still asking for password ("Enter your user password or administrator  password"), but it should not as I understand. 
 
If I Cancel the password (i.e. do not provide the password) and try once  again to mount, it works then (i.e. only does not work for the first  time). 
 
Also noticed, that for the first time, the process "/usr/bin/truecrypt  --core-service" is not running (ps aux | grep truecrypt). But after the  second try (the successful) the process "/usr/bin/truecrypt  --core-service" is running (then there are actually 3 of these). 
 
Any ideas what could be wrong?

---

