---
title: "Virgin broadband fault"
date: 2010-06-04
forum: General Help
---

### Post by bigguly on 2010-06-04
Hi All, I do require your help on the following issue which has been affecting my cousin for a couple of weeks, and I've not been able to find the answer using the search. 
He has Virgin broadband, it works, but the problem is that he has to restart his PC to get it to work.  He is connected to the supplied Netgear router, when he turns on his machine, the Kubunutu 10.4 does not pick up the network connection. He reboots, and then he gets a network connectiona and he can go about his surfing. 
I look forward to your replies.

---

### Post by bigguly on 2010-06-11
Hi All,  
I see that there have been many views but no answers.  Please can you let me know what further questions I need to ask my cousin to make things work for him?  
):P

---

### Post by mechdave on 2010-06-11
Sounds like that Kbuntu may not be asking for a ip address, what happens if he turns on the computer then the router then opens a terminal and types the following ```
 sudo dhclient 
``` then enters his password when requested and see what happens? He should get internet connection if I am right in thinking that Kubuntu is not asking for a ip addresss on a regular interval :)

---

### Post by bigguly on 2010-06-12
Thanks for the reply.  Once he has restarted, it works absolutely fine until he turns it off, then he has to go through the same procedure again.  I will get back to you as soon as I pay him a visit again.

---

### Post by bigguly on 2010-07-03
Hi, 
After trying to login, with the router turned off, and then turning the router on, the following is what is displayed on my cousin's machine after the sudo dhclient command- 


abdul@Abdul-Waheed:~$ sudo dhclient
[sudo] password for abdul: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

No broadcast interfaces found - exiting.
abdul@Abdul-Waheed:~$ 



After a restart of the PC, everything is working fine, and the following is from the sudo dhclient output.


abdul@Abdul-Waheed:~$ sudo dhclient
[sudo] password for abdul: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:30:67:34:6c:50
Sending on   LPF/eth0/00:30:67:34:6c:50
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 37360 seconds.
abdul@Abdul-Waheed:~$ 


I hope you can help me further.

---

### Post by spiky001 on 2010-07-03
I dont know if this will help abit if network not connecting

```
sudo /etc/init.d/networking restart
```

might not fix but might save rebooting

---

### Post by bigguly on 2010-07-03
Hi, 
I've tried to restart the network, but this does not help. The terminal said it had been restarted, but nothing happened.  I have had to restart the PC to get to give you this answer!

---

