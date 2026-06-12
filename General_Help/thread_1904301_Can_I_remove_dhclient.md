---
title: "Can I remove dhclient"
date: 2012-01-04
forum: General Help
---

### Post by rng on 2012-01-04
When I give the command 'sudo netstat -apute' to check what applications are connected to network, it shows 'dhclient' is always there on my system running ubuntu 10.04LTS.  It is not there on my other system, also running ubuntu (later version, I think 11.04 or 11.10).

Can I remove 'dhclient' without any untoward effect? And how can I remove it?

---

### Post by 2F4U on 2012-01-04
I am running 11.10 and I have dhclient installed, so you may want to double check whether your really don't have it. Anyways, dhclient is responsible for dynamically assigning an IP address to your computer. If you are using a dynamic IP addresses instead of static IP address you better keep it on the system.

---

### Post by kerry_s on 2012-01-04
> **rng said:**
> When I give the command 'sudo netstat -apute' to check what applications are connected to network, it shows 'dhclient' is always there on my system running ubuntu 10.04LTS.  It is not there on my other system, also running ubuntu (later version, I think 11.04 or 11.10).

Can I remove 'dhclient' without any untoward effect? And how can I remove it?

you'll kill internet on your system.

---

### Post by rng on 2012-01-05
On this newer system I am running ubuntu 11.04 natty. On 'netstat -apute' command there is no dhclient and I am able to use the internet (though I have setup ip addresses and network proxy thru network settings).

---

### Post by kerry_s on 2012-01-05
so your using a static  ip.
dhclient is not hurting nothing being there, why do you want to get rid of it so badly?

---

