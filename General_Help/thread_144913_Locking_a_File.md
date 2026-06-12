---
title: "Locking a File"
date: 2006-03-15
forum: General Help
---

### Post by megahertza on 2006-03-15
I have DNS problems like a fair few others, I have to set my DNS config all the time. I have installed resolvconf which helps but doesn't solve the problem, it reduces the ammount that i have to reset the config file back to my settings. Now I have to set my DNS when i connection is idle for a while and when ubuntu boots up.

The idle problem does not worry me, if gaim messenger is loged in. This is my solution and bear in mind I'm a still a linux noob. I want to know if this is possible and your thoughts on it.

1st. Lock the resolv.conf file so that the system can not edit, delete, move, replace the file. So that the DNS config in the file can not be changed.

2nd. On boot up, the resolv.conf file is replaced with a version with the user's DNS. So that when the ubuntu boots ups it will load with the correct DNS.

3rd. When ever the resolv.conf file is replaced with a default of "nameserver 192.168.1.1" (I believe). Is it possible to change the default to your own DNS.

Thanks Guys

---

### Post by Ramses de Norre on 2006-03-15
Does your /etc/network/interfaces change by its own?
Otherwise put your DNS settings in there.

---

### Post by megahertza on 2006-03-15
Can you give a example of hos i would put my DNS setting in interfaces? The same way it is in resolv.conf

eg

namesever 203.134.64.66

---

