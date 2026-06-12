---
title: "Problems Changing To An IP Proxy In Lucid"
date: 2010-06-01
forum: General Help
---

### Post by giddyup306 on 2010-06-01
Hello,

I'm trying to change my IP to a remote proxy.  However, my new IP doesn't show up.

In Firefox I tried Edit > Preferences > Advanced > Settings and clicked on Manual Proxy Configuration, typed in my new IP, then ticked Use this proxy server for all protocols.  

Still didn't change.

I then went to System > Preferences > Network Proxy Preferences and  ticked on Manual Proxy Configuration and also ticked Use the same proxy for all protocols. 

In my final attempt I went to the terminal and typed in ifconfig.  Then ifconfig eth0 XXX.XXX.X.XXX up and it told me

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied

No, I didn't have X's in there, I used my proxy.  Just using it as an example. 

Still nothing.  Any of these methods should work, right?

I'm running Firefox 3.5.3, and Ubuntu 10.04.

Any help is greatly appreciated.

---

### Post by giddyup306 on 2010-06-01
I'm not sure what happened, but now it's working fine.

---

