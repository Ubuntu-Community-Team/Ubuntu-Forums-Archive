---
title: "a mac problem"
date: 2010-09-06
forum: General Help
---

### Post by meoow on 2010-09-06
My college restricts mac addresses of accessing to network, under windows i must change the mac to the given address to get on internet.The method to Linux which I found via google like this:
> sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE
sudo ifconfig eht0 up
sudo /etc/init.d/network restart
After typing these commands into terminal my browser still can't open any web pages.It didn't work at all.

Is there any other way can deal with this problem?

---

### Post by zaphod777 on 2010-09-06
does it show the correct mac address when you do ifconfig?

after you change it you might want to run
```

sudo /etc/init.d/networking restart
 
```

---

