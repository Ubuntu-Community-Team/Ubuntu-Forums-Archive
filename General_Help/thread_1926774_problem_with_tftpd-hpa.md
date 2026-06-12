---
title: "problem with tftpd-hpa"
date: 2012-02-16
forum: General Help
---

### Post by gbuck on 2012-02-16
I am trying to setup tftp annd having some issues getting the process started. when I start tftpd-hpa I see 'tftpd-hpa-start/running' with no procedd ID associated with it.
 
I left the /etc/init/tftpd-hpa.conf and /etc/init/tftpd-hpa files alone as their default after running apt-get install tftpd-hpa.
 
The /etc/default/tftpd-hpa file is as follows:
RUN DAEMON="yes"
OPTIONS="-l -a 172.31.128.11 -s /greg/tftpboot"
 
If I look at the running processes with ps -ef | grep tftp I get nothing.
 
I would appreciate any help I can get on this..

---

### Post by gbuck on 2012-02-18
Fixed.. it was a syntax error in /etc/default/tftpd-hpa.conf..  'RUN_DAEMON' not 'RUN DAEMON'

In retrospect I should have realized that based on my multiple spelling errors in the post above.

Time to slow down while typing..

---

