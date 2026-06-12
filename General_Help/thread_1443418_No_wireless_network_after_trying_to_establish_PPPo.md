---
title: "No wireless network after trying to establish PPPoE connection in Karmic Koala"
date: 2010-03-31
forum: General Help
---

### Post by cheetex on 2010-03-31
Hi,
I installed ubuntu Karmic Koala 2 weeks ago, and while I have been able to connect to my school wireless, I have not been able to establish a PPPoE connection (username and password).
After my most recent try, following this guide: [http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html)
My wireless connection has gone as well.
My network manager applet shows my school network, and shows that it is trying to connect, but it cannot establish a connection.
Any help would be greatly appreciated, and i apologize in advance for any information that i am lacking. please let me know, and i'll try to get the information.

I'm running ubuntu on a separate partition, alongside windows XP home.

Thanks

---

### Post by Bungler on 2010-03-31
You could also try the pppoe conf setup
```
sudo pppoeconf
```
That works for me to set up a pppoe connection. In order to make the connection visible you can use the bugfix mentioned on Ubuntugeek link.

Or in you current configuration, is DHCP on?.. Check other settings...

---

### Post by cheetex on 2010-04-01
Hi,
sorry, I don't think I made myself clear. Although my PPPoE connection still does not work, that is not my main worry.
After following the guide mentioned above, I cannot connect to wireless internet. I could connect before, and the same internet is still showing up, but I cannot connect to it. Network manager shows that it is trying to connect, but cannot establish a connection.

---

