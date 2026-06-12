---
title: "Why multiple entries entries of the same command in my top display?"
date: 2011-09-15
forum: General Help
---

### Post by neanderslob on 2011-09-15
Hi there,

I was sorting my htop display by memory usage and found that nearly every command had multiple PIDs of identical respective memory usage.  I don't think there's necessarily anything wrong (though I admit I don't know enough about how this sort of thing is organized to say one way or another).  But I am curious as to why this is the case.  (More of a question of interest than anything.)

Thanks!

:guitar:

---

### Post by ibutho on 2011-09-15
This is quite normal on Linux systems. Some processes spawn child processes, so when you run top or similar apps, you will see multiple entries. Apache HTTPD server and MySQL are some of those apps (Multi-threaded apps).

---

### Post by neanderslob on 2011-09-15
Thanks so much then.

---

