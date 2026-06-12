---
title: "Vmware server installation issue"
date: 2010-06-08
forum: General Help
---

### Post by GirishSharma on 2010-06-08
Hello,

I am in process of configuration of vmserver on my ubuntu 10.04 32 bit machine and for this i run a script which i downloaded from this link :
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

because earlier; when i was trying to install vmserver; i stuck at error "Unable to build vmmon module".  

This script run without any error and finally i got "Enjoy Team..." message.  But here i am struggling for 2 issues :

1.When the above script was running, i forgot to add vmserver administrator, so now i am not able to login to vmserver ([http://localhost:8222/](http://localhost:8222/)).  The user; who run the above script was "girish" (i.e. myself), but when i gives username as "girish" and password; it is saying that you are not authorized; or privilege not having... error.

2.If i shutdown the machine and restart and in firefox i says :
[http://localhost:8222/;](http://localhost:8222/;) firefox is not able to bring back that login page; which came after finishing of the script.

$ ifconfig -a
is showing only eth0 and lo, not vmnet1 or vmnet8; so i think if they are not coming in output of ifconfig -a command; i will not able to get that login page; but whats wrong here; i am very much confused and frustrated to get all these working.

Kindly help me.
Regards
Girish Sharma

---

### Post by GirishSharma on 2010-06-08
I have downloaded the vmserver from its official site with proper activation key.  I think its not an issue of registration or licence issue here, because there is no such error, which points me for an invalid activation key or etc.

---

### Post by GirishSharma on 2010-06-09
Anyone please help me to install vmware software on my 32 bit machine having Ubuntu 10.04?

What should i install/run to get vmware tool, so that i may configure windows xp as guest os?

---

### Post by dcstar on 2010-06-09
> **GirishSharma said:**
> Anyone please help me to install vmware software on my 32 bit machine having Ubuntu 10.04?

What should i install/run to get vmware tool, so that i may configure windows xp as guest os?

Read any of the instructions in the Virtualization forum?

---

