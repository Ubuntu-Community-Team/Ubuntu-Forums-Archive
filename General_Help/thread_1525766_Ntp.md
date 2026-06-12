---
title: "Ntp"
date: 2010-07-07
forum: General Help
---

### Post by PJDouglas on 2010-07-07
Hi,

I have setup Ubuntu Server as a NTP timesource for our windows servers.

The service is running and synchs with an external time clock.

The problem I have is that my servers cannot connect to the Ubuntu box.

I have a Netgear NAS box that reports it cannot connect when I point the NTP service to it.

When I stop the time service on the windows servers and run w32tm -s to synch the clocks I receive the message 'RPC to local server returned 0x6b5' which I believe to be a successful synch. After restarting the time service the clocks do you change/update??

Nothing is reported in the event logs.

There are no firewalls sat in between the Ubuntu and windows servers.

Any help would be appreciated.


Many thanks

Paul.

---

### Post by btindie on 2010-07-07
Do you have another linux box that you can use to check that it works with
```
ntpdate -q <ip_address_of_ntp_server>
```
Is *ntpd* configured correctly to act as a NTP server?
 
Take a look at [http://blog.loftninjas.org/2007/11/08/ntpd-and-windows-server-2003-sp1-w32time/](http://blog.loftninjas.org/2007/11/08/ntpd-and-windows-server-2003-sp1-w32time/) for windows configuration. Manually change the time on the windows host before restarting the w32tm service so you can see if it works.

---

### Post by PJDouglas on 2010-07-09
> **btindie said:**
> Do you have another linux box that you can use to check that it works with
```
ntpdate -q <ip_address_of_ntp_server>
```Is *ntpd* configured correctly to act as a NTP server?
 
Take a look at [http://blog.loftninjas.org/2007/11/08/ntpd-and-windows-server-2003-sp1-w32time/](http://blog.loftninjas.org/2007/11/08/ntpd-and-windows-server-2003-sp1-w32time/) for windows configuration. Manually change the time on the windows host before restarting the w32tm service so you can see if it works.

Thanks  for your reply.

Our linux/Ubuntu boxes are synching fine. Problem seems to be with our windows servers.

Will try the above and see what happens.

Many Thanks

Paul.

---

