---
title: "Jailkit and /bin/bash"
date: 2010-11-27
forum: General Help
---

### Post by domzz on 2010-11-27
I installed jailkit. Jailkit a user and now when I try to log in as root, it give me: 

```
/bin/bash: No such file or directory
```

My #ldd /bin/bash


```
linux-vdso.so.1 =>  (0x00007fff2bbff000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x00007fc39fe8e000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007fc39fc8a000)
        libc.so.6 => /lib/libc.so.6 (0x00007fc39f906000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fc3a00d9000)    
```

---

### Post by domzz on 2010-11-27
I also tried:

```
sudo apt-get install --reinstall bash
```

and
[http://newyork.ubuntuforums.org/showthread.php?t=1267341](http://newyork.ubuntuforums.org/showthread.php?t=1267341)

My /etc/passwd is

```
root:x:0:0:root:/root:/bin/bash
```

---

### Post by domzz on 2010-11-27
Ok, I fixed it...

I forgot to comment out something in sshd_config (nothing to do with jailkit or /bin/bash!)

---

### Post by karthick87 on 2010-11-27
Write the solution and Mark it as solved.

---

