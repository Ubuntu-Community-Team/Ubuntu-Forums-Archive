---
title: "Active internet connections (servers)"
date: 2011-09-16
forum: General Help
---

### Post by rng on 2011-09-16
The netstat -a command on my computer shows following: 

$ sudo netstat -a 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 * : www                   *:*                     LISTEN     
tcp        0      0 localhost : ipp           *:*                     LISTEN     
tcp        0      0 localhost : postgresql    *:*                     LISTEN     
tcp        0      0 localhost : smtp          *:*                     LISTEN     
tcp        0      0 * : https                 *:*                     LISTEN     
tcp6       0      0 localhost : ipp           [::]:*                  LISTEN     
tcp6       0      0 localhost : postgresql    [::]:*                  LISTEN     
tcp6       0      0 localhost : smtp          [::]:*                  LISTEN     
....
....

How can I close/stop/avoid these? Thanks for your help.

---

