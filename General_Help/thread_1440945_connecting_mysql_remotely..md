---
title: "connecting mysql remotely."
date: 2010-03-28
forum: General Help
---

### Post by vksingh on 2010-03-28
Hi,

I have installed mysql server on a machine having Ubuntu 9.10. I want to access the mysql server from other machine without ssh.

Thanks,

Vivek

---

### Post by Hellkeepa on 2010-03-28
HELLo!

Then you need to forward port 3306, or whatever port you've set MySQL up to use. You'll also need to make sure that your user account has access from the IP-address/hostname that you'll be using, before trying to connect. Limiting this to a single host is highly recommended, lest someone should try and hack your MySQL server.

PS: Not a programming question, but a server/network admin one.

Happy codin'!

---

### Post by r_s on 2010-03-28
[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)
Well I think, using ssh would be better as it won't mess up with security purposes of your database.

---

### Post by Elfy on 2010-03-28
moved to general help

---

