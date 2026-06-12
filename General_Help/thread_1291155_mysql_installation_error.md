---
title: "mysql installation error"
date: 2009-10-14
forum: General Help
---

### Post by r_s on 2009-10-14
I am trying to install mysql5.0 in ubuntu 9.04 but when I try the command sudo apt-get install mysql-server , it returns an error message which goes like this
 
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
 * Stopping MySQL database server mysqld                                                                                                                        [ OK ] 
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please Help

---

### Post by jonobr on 2009-10-15
Im no mysql expert but are you installing this yourself using source or are you using synaptic.

An errors in you syslogs?

---

### Post by rmadams1 on 2009-11-27
I'm getting the same error and have tried both synaptic and source. I'm running ubuntu 9.10. I started by trying to install via synaptic, then uninstalling when I couldn't get it to work, then moving to a terminal session, and am still having issues.
 
I've tried numerous things after searching the net, but as you can tell, I'm a newbie and now have my install so jacked I'm not sure where to fo next.
 
Apologies for the hijack, but the op seems to have vanished, and I'm hoping someone would be willing to give me a hand with the same issue.
 
TIA-

---

### Post by rmadams1 on 2009-11-29
Solved my own issue. MySQL was needed for nagios, and rather than fight with it any further I installed FAN.

---

