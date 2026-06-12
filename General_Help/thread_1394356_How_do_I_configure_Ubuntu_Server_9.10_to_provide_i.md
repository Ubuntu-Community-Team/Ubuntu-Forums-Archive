---
title: "How do I configure Ubuntu Server 9.10 to provide internet through a proxy to my LAN?"
date: 2010-01-30
forum: General Help
---

### Post by intermentals on 2010-01-30
I'm trying to get my set up to provide internet to my LAN through a squid proxy. I have DHCP set up and working and I think squid is configured right, my question is what else do I need to configure for the server to function and how do I do it?

Also the server I'm replacing is running OpenBSD 4.5 and uses a wpad.dat file for automatic configuration for squid, how would I go about using this same set up in Ubuntu?

Thanks

---

### Post by gmargo on 2010-02-01
You're not giving much information to go on. I run squid on my Linux box and the other hosts on my LAN can use it just fine.  

Is squid working?  What errors are you getting?  Can you access squid locally?  Do you have to open port 3128 with your firewall software?

---

