---
title: "Setting up a TUN interface"
date: 2011-03-14
forum: General Help
---

### Post by Squeazer on 2011-03-14
I have a problem setting up a TUN interface for OpenVPN.

Running OpenVPN gives me this error: 
"Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)"

Which i tracked down to: "WARNING: Couldn't open directory /lib/modules/2.6.18-164.15.1.el5.028stab068.9: No such file or directory" (if i run /sbin/modproble tun). Does anyone know how to fix this?

---

### Post by Sven6210 on 2011-03-22
Are you running OpenVPN on a Virtual Machine? If so you might have a look at:

[http://www.webhostingtalk.com/archive/index.php/t-720412.html](http://www.webhostingtalk.com/archive/index.php/t-720412.html)

---

