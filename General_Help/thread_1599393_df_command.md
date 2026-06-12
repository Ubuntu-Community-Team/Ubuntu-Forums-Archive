---
title: "df command"
date: 2010-10-17
forum: General Help
---

### Post by Hippytaff on 2010-10-17
What do the 'none' bits mean?

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             14417392   4034720   9650308  30% /
none                    502632       264    502368   1% /dev
none                    508228       232    507996   1% /dev/shm
none                    508228       220    508008   1% /var/run
none                    508228         0    508228   0% /var/lock
/dev/sda1                93207     24577     63818  28% /boot
/dev/sda7             60486740    392288  57021892   1% /home
/dev/sr0               3070458   3070458         0 100% /media/Peppa Pig s2&3

```

---

### Post by marshmallow1304 on 2010-10-17
Those are virtual file systems.  Here are explanations for [/dev]("http://tldp.org/LDP/sag/html/dev-fs.html"), [/dev/shm]("http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html"), [/var/run]("http://www.unix.com/302115533-post3.html"), and [/var/lock]("http://www.pathname.com/fhs/2.2/fhs-5.9.html").

---

### Post by Hippytaff on 2010-10-17
> **marshmallow1304 said:**
> Those are virtual file systems.  Here are explanations for [/dev]("http://tldp.org/LDP/sag/html/dev-fs.html"), [/dev/shm]("http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html"), [/var/run]("http://www.unix.com/302115533-post3.html"), and [/var/lock]("http://www.pathname.com/fhs/2.2/fhs-5.9.html").

Thankyou

---

