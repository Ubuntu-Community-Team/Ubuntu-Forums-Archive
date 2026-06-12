---
title: "missing /etc/inittab and /etc/event.d"
date: 2010-09-30
forum: General Help
---

### Post by withjigs on 2010-09-30
Hi everybody,
I am preparing for Ubuntu certified professional and I read about how /etc/inittab is replaced by /etc/event.d.  I found that directory in 9.10 but after upgrading my Ubuntu to lucid 10.4 that directory is missing again.
Is that normal ? I dont have /etc/inittab either??!
Thanks 
Jigar

---

### Post by sisco311 on 2010-10-01
In 10.04 Upstart jobs are defined in files placed in /etc/init.

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by withjigs on 2010-10-02
thank you sisco311 for you reply.
it is frustrating though that it is changing so frequently. 
Thanks for the link...

---

