---
title: "number of open files limit"
date: 2009-12-03
forum: General Help
---

### Post by fraktalek on 2009-12-03
Hi,

what is the correct way to increase the per-process number of open files limit?

I tried to add

```

fs.file-max = 4096

```

to /etc/sysctl.conf, and

```

* - nofile 4096

```

to /etc/security/limits.conf

And it worked but only until I restarted and tried to log into gnome. Then suddenly gnome stopped working and after a while of researching I came across a "too many files open" error.

Should I have changed only the limits.conf file? Because before the modifications "cat /proc/sys/fs/file-max" gave a big number, well over 200 000, after the modifications it gave only 4096

So I guess it changed the limit for the total number of open files. How do I change the per-process limit?

---

### Post by ratcheer on 2009-12-03
When I enter the command "ulimit", it tells me that it is unlimited. I have done nothing to my system to change anything like that.

---

### Post by fraktalek on 2009-12-03
> **ratcheer said:**
> When I enter the command "ulimit", it tells me that it is unlimited. I have done nothing to my system to change anything like that.

I also see some "unlimited" but not by the "open files", where it is only 1024:
```

# ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

### Post by fraktalek on 2009-12-04
One resource I found, although it doesn't explain much:

[http://knol.google.com/k/fred-grott/open-file-limits-settings-on-ubuntu/166jfml0mowlh/3#](http://knol.google.com/k/fred-grott/open-file-limits-settings-on-ubuntu/166jfml0mowlh/3#)

---

### Post by fraktalek on 2009-12-04
Hmm, I see first that this problem is not so uncommon:
[http://ubuntuforums.org/showthread.php?t=1274847](http://ubuntuforums.org/showthread.php?t=1274847)

and second that the search functionality on ubuntuforums is really not very good. The forums are great but it's really better to search via google...

---

### Post by fraktalek on 2009-12-04
Setting /etc/sysctl.conf to
```

*  soft  nofile 4096
*  hard  nofile 4096

```

seems to work fine for me.

---

