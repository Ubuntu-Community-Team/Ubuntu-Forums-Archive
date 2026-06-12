---
title: "kill -HUP 1"
date: 2010-03-11
forum: General Help
---

### Post by mr.wu on 2010-03-11
I want to change the number of tty processes from default 6 to just 1.  In redhat variant I'm familiar with, I modify /etc/inittab and do "kill -HUP 1"
There is no need to reboot the system.

For Ubuntun 9.10 server I am using, I can remove tty2.conf to tty6.conf from /etc/init.  But I cannot kill tty2 to tty6 processes except by rebooting the server.  Any other way?

---

### Post by ibuclaw on 2010-03-11
In Ubuntu, it is simply:
```
stop tty2
```
and so forth.

Similarly, to start the process
```
start tty2
```
or restart
```
restart tty2
```
or check on the status
```
status tty2
```

Regards
Iain

---

### Post by mr.wu on 2010-03-11
That's very nice.  Thanks for quick reply.

---

