---
title: "mysql-server install error"
date: 2011-05-15
forum: General Help
---

### Post by Knacker on 2011-05-15
I'm trying to install the squeezebox server software in Ubuntu 9.10 and I'm getting an error when it tries to install mysql-server. Seems like people have run into this before ([http://ubuntuforums.org/showthread.php?t=1293889](http://ubuntuforums.org/showthread.php?t=1293889)) but so far, I can't find a solution... Can anyone help me sort this out? 

Here is the error: 

Get:1 [http://debian.slimdevices.com](http://debian.slimdevices.com) stable/main squeezeboxserver 7.5.4 [35.6MB]
Fetched 35.6MB in 24s (1,477kB/s)                                              
Preconfiguring packages ...
(Reading database ... 121080 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.83-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1

---

### Post by Knacker on 2011-05-15
Looks like I posted a bit prematurely -- apologies. I *think* I fixed it. Here's what I did: 

Removed debian-5.1.flag and mysql_upgrade_info from /var/lib/mysql and tried again. All installed properly. 

Here's hoping I didn't screw something else up! Apologies again for not working harder at this before posting.

---

