---
title: "Cannot resolve local server names.."
date: 2011-08-23
forum: General Help
---

### Post by chait on 2011-08-23
[SIZE=2]Hello All,

   I have installed Ubuntu 11.04 Natty just now. We have two local name servers on the LAN. I have listed both of them in the /etc/resolv.conf file. Also they are being resolved using 'dig' and 'nslookup' utilities.
In Mozilla Firefox, I have listed the local subnet to not to look for proxy.
Now when I try to access any server using the name of that server, I get error.
But when I access using the ip address it works.
I am banging my head for an hour now.](*,)
Any suggestion is appreciated. 

Thanks.

[/SIZE]

---

### Post by el_koraco on 2011-08-23
Shouldn't you put them in /etc/hosts as well?

---

### Post by chait on 2011-08-23
Hi el_koraco,
   Thanks for replying. But we don't have to put all the addresses in the hosts file. The name resolution should be managed by the local name server. I have another workstation with the similar settings, and its working fine!! U only need to specify the 127.0.0.1 entry in the hosts file i.e. of localhost.
    Thanks.

---

### Post by chait on 2012-02-29
Hi All,
   Sorry for not posting so long, but I resolved the issue and forgot to post here. Actually I did not have an entry of the server name in the 'No Proxy For' section of Mozilla Firefox. Now it works fine.

Thanks.):P

---

