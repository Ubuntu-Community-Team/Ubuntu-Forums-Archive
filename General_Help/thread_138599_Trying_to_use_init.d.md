---
title: "Trying to use init.d"
date: 2006-03-02
forum: General Help
---

### Post by Jonathan Métillon on 2006-03-02
I use ndiswrapper to load a Windows 2000 driver (mrv8000c)
for my wireless card (pciid: 11ab:1faa)
 
But when Ubuntu starts, it gets stuck on /etc/init.d/networking
 
So I created a script, wlanup, which I placed in /etc/init.d,
and that basically load the driver with ndiswrapper and activate
the wireless card.

I followed instructions from [http://beaxp.free.fr/admin_service.html](http://beaxp.free.fr/admin_service.html)
 
I manually launched the script with "start", "stop" and "status",
it works okay.
 
Then I linked the script from /etc/rc5.d to start it when entering
graphical mode and from /etc/rc0.d to stop it at shutdown.
 
Then I shutdown and reboot, nothing new.
Why my script has not been used?
 
Thank you
 
The files:
 
```
# ls /home/john/mrv8000c
Mrv8000c.cat  Mrv8000c.INF  Mrv8000c.sys
# ls /etc/init.d/wlanup
-rwxr-xr-x 1 root root 436 2006-03-02 14:35:01 /etc/init.d/wlanup*
# ls /etc/rc5.d/S99wlanup
lrwxrwxrwx 1 root root 16 2006-03-02 14:12:15 /etc/rc5.d/S99wlanup -> ../init.d/wlanup*
# ls /etc/rc0.d/K86wlanup
lrwxrwxrwx 1 root root 16 2006-03-02 14:15:14 /etc/rc0.d/K86wlanup -> ../init.d/wlanup*
```
 
The wlanup file:
 
```
#!/bin/sh
# chkconfig: runlevels order_start_link order_stop_link
# description: short description of service
. /lib/lsb/init-functions
case "$1" in
start)
echo -n "Starting service: " 
ndiswrapper -i /home/john/mrv8000c/Mrv8000c.INF
ifup wlan0
echo
;;
stop)
echo -n "Shutting down service: " 
ifdown wlan0
ndiswrapper -e mrv8000c
echo
;;
status)
ndiswrapper -l
;;
*)
echo "*** Usage: service_name {start|stop|status}" 
exit 1
esac
exit 0
```

---

### Post by romdos on 2006-03-02
the default runlevel in ubuntu is 2 (according to /etc/inittab )
try putting your script in rc2.d in order to have it executed at boot

---

### Post by Jonathan Métillon on 2006-03-03
Thank you romdos, you got that point \\:D/ 

I moved /etc/rc5.d/S99wlanup to /etc/rc2.d/S99wlanup and now the wireless card is correctly initialized at boot, and the original networking initialization doesn't hang any more.

But I still have to manually unload the device at reboot, otherwise the system get stuck before completing shutdown.

I added a bit of logging to my wlanup script, but it outputs nothing useful.

```
logfile=/home/john/mrv8000c/wlanup.log
. /lib/lsb/init-functions
case "$1" in
start)
echo "Starting wlan0" >> $logfile 2>&1
ndiswrapper -i /home/john/mrv8000c/Mrv8000c.INF >> $logfile 2>&1
ifup wlan0 >> $logfile 2>&1
echo
;;
stop)
echo "Shutting down wlan0" >> $logfile 2>&1
ifdown wlan0 >> $logfile 2>&1
ndiswrapper -e mrv8000c >> $logfile 2>&1
echo
;;
status)
ndiswrapper -l
;;
*)
echo "*** Usage: service_name {start|stop|status}"
exit 1
esac
exit 0
```

And the wlanup.log file where you can see that only the start case is logged, nothing about the stop case so it's not even executed before freezing:

```
Starting wlan0
Installing mrv8000c
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:40:f4:xx:xx:xx
Sending on   LPF/wlan0/00:40:f4:xx:xx:xx
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 36095 seconds.
```

---

### Post by Titus A Duxass on 2006-03-03
Why are you taking this complicated approach?

Why don't you edit the the network interface file as described in other threads?

---

### Post by Jonathan Métillon on 2006-03-07
Because I though that if I update/change my Linux distro, it would be easier to just copy my custom files than edit the networking file.

But I can be wrong, I'm really newbie to this.
Can you please point me to one of these threads?

---

