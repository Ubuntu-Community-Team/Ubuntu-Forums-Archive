---
title: "hostname: short name and long name, whats the difference?"
date: 2010-09-27
forum: General Help
---

### Post by sim085 on 2010-09-27
Hello, I installed a new instance of Ubuntu server (10.04) and set the hostname equal to "ubuntu-10.04-server-i386". However when I type the command hostname I get that the hostname is equal to "ubuntu-10". I then realised that the command *hostname --long* gives me the full name (as defined when doing the linux installation) while *hostname --short* gives me the name as displayed in terminal. My question is; what is the difference between these two? Are both valid?

---

### Post by plucky on 2010-09-27
> **sim085 said:**
> Hello, I installed a new instance of Ubuntu server (10.04) and set the hostname equal to "ubuntu-10.04-server-i386". However when I type the command hostname I get that the hostname is equal to "ubuntu-10". I then realised that the command *hostname --long* gives me the full name (as defined when doing the linux installation) while *hostname --short* gives me the name as displayed in terminal. My question is; what is the difference between these two? Are both valid?

From output of ```
man hostname
``` > -s, --short
              Display the short host name. This is the host name  cut  at  the
              first dot.


I assume if it has no dot it will show the whole hostname.

Good luck

---

### Post by btindie on 2010-09-27
The short one is just the name of the host, the long is the Fully qualified Domain Name (FQDN) which includes the domain name it's part of - e.g. ubuntuforums.org
 
You've given your host the name of "ubuntu-10" and the domain of "04-server-i386"! A dot '.' in a domain name is a seperator character. See [http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)

---

### Post by sim085 on 2010-09-27
> **btindie said:**
> You've given your host the name of "ubuntu-10" and the domain of "04-server-i386"! A dot '.' in a domain name is a seperator character. See [http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)

In other words I was doing a total mess!! :$ Thanks for the reply. I will give some simpler names.

---

### Post by Morbius1 on 2010-09-27
Something else to think about is whether you plan to use samba in your network. By default samba uses the hostname as the netbios name it broadcasts to the network. Netbios names have to be 15 characters or less in length. You can override the hostname as netbios name default by adding a "netbios name =" parameter in smb.conf if you really want a long hostname.

---

