---
title: "Anyway to automaticaly refresh my ethenet conection every X hours?"
date: 2010-03-06
forum: General Help
---

### Post by waxyfresh on 2010-03-06
My DSL modem is constantly loosing its signal every time i start a torent downloading,im not sure if its trying to connect to too many peers for DSL modem to handle or what. but it does this on both windows and linux,what id like is a way to have the computer ping a site like Google and if no signal is sent back then the script will automatically refresh my eth1 connection. 

Is this possible? If so id assume it would be easy to script but then again i know nothing about scripting.. If its something very simple could someone script it for me? I leave my computer untended for days on end and im not around to refresh my modem by hand so this would be a big help.

---

### Post by patchwork on 2010-03-06
Ok, I've got something that may work if your eth1 is wired, but I'm having trouble making it work for wireless.  This is assuming a dhcp connection ( but it can be modified for static ips).  Try it in your /etc/crontab set to run every however many number of hours you want as root.


```
if ! ping -c 4 www.google.com; then ifup eth1; dhclient eth1; fi;
```
Give it a try, it may need to be tweaked.

OK, for wireless, you can try this:

```
 if ! ping -c 4 www.google.com; then ifconfig eth1;
 iwconfig eth1 essid NETWORK_ID key WIRELESS_KEY;
 dhclient eth1;
fi;
```


from:  [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

---

