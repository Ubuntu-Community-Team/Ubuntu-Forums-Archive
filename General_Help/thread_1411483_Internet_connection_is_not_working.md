---
title: "Internet connection is not working"
date: 2010-02-20
forum: General Help
---

### Post by Thamizhinpan on 2010-02-20
I'm using Ubuntu Karmic 9.10, And I'm using a wireless modem for internet.
Suddenly i got a trouble on my internet usage. Even I can able to connect internet in ubuntu, applications (like firefox) can't able to access it.
But even now, I can able to use it in windows. So I think something must be gone wrong in ubuntu. 
How to solve it?

---

### Post by sj1410 on 2010-02-20
> **Thamizhinpan said:**
> I'm using Ubuntu Karmic 9.10, And I'm using a wireless modem for internet.
Suddenly i got a trouble on my internet usage. Even I can able to connect internet in ubuntu, applications (like firefox) can't able to access it.
But even now, I can able to use it in windows. So I think something must be gone wrong in ubuntu. 
How to solve it?

how are you trying to connect. check if its really connect by issuing the following commands

ifconfig

route -n


Regards

---

### Post by r_s on 2010-02-20
Is it that it is showing connected on your screen , yet you are unable to access any sites.

---

### Post by lovinglinux on 2010-02-20
[Disable ipv6 ]("http://lovinglinux.megabyet.net/?page_id=220#Web-sites-keeps-loading-but-never-show-up-2")

---

### Post by Thamizhinpan on 2010-02-20
> **r_s said:**
> Is it that it is showing connected on your screen , yet you are unable to access any sites.
Yes, that's correct

---

### Post by r_s on 2010-02-21
[http://ubuntuforums.org/showthread.php?t=158521](http://ubuntuforums.org/showthread.php?t=158521)

---

### Post by Iowan on 2010-02-21
> **sj1410 said:**
> ifconfig [COLOR="Blue"]-a[/COLOR]
route -nThis information will help. Contents of */etc/resolv,conf* might also be useful...

---

