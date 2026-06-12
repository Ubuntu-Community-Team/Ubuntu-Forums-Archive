---
title: "Xen - installed but cant be managed with VMM"
date: 2012-05-30
forum: General Help
---

### Post by sdpagent on 2012-05-30
Dear all,
I followed this tutorial to install xen on ubuntu server (64 bit):
[https://help.ubuntu.com/community/XenProposed](https://help.ubuntu.com/community/XenProposed)

I had no problems and even the test to make sure xen was running is working.

I also used this tutorial to set up a static ip:
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

Unfortunately, my VMM on a remove machine will not connect to it, however it can SSH In as both the root and non-admin users. The VMM will ask for the password, take it and then just states not connected. 

Normally I use centOS 5.8 as setting up a xen server is REALLY easy on that, but if I can switch to ubuntu that would be better, its super-quick to restart.

Stu

-----------------------
Added edition:
I noticed that if i type the WRONG password in, it keeps popping up asking for the password, if I type the correct password in, then it immediately stops and states not connected, suggesting its logging in correctly and determinng that xen isnt running?

---

