---
title: "Install 32-bit MySQL libraries on 64-bit Ubuntu?"
date: 2009-09-24
forum: General Help
---

### Post by Sarteck on 2009-09-24
I feel really dumb for asking this, but I've been trying to find out how I can do this all morning.  XP

A bit of background on the problem:
I'm trying to tinker with Sphere Server, a game engine.  In the install process, we are supposed to run, ```
ldd spheresvr
``` and "fix" any libraries that are not found.

```
root@Auron:/usr/lib# ldd /home/sphere/spheresvr
        linux-gate.so.1 =>  (0xf7f2d000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ee8000)
        libmysqlclient.so.15 => not found
        librt.so.1 => /lib32/librt.so.1 (0xf7ede000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7def000)
        libm.so.6 => /lib32/libm.so.6 (0xf7dc9000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7dba000)
        libc.so.6 => /lib32/libc.so.6 (0xf7c57000)
        /lib/ld-linux.so.2 (0xf7f2e000)

```
As you can see, it's not finding my libmysqlclient for some reason.  Odd thing is, I can find it just fine:
```

root@Auron:/usr/lib# ldconfig -v | grep mysql
/sbin/ldconfig.real: Can't stat /usr/lib/kde4/lib: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf95d.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf77cd.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf95cd.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotadad.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf77d.so: No such file or directory
        libmysqlclient.so.16 -> libmysqlclient.so.16.0.0
        libmysqlclient_r.so.15 -> libmysqlclient_r.so.15.0.0
        libmysqlpp.so.3 -> libmysqlpp.so.3.0.0
        libmysqlclient_r.so.16 -> libmysqlclient_r.so.16.0.0
        libmysqlclient.so.15 -> libmysqlclient.so.15.0.0
/sbin/ldconfig.real: Cannot stat /usr/lib32/libmysqlclient_r.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib32/libmysqlclient.so: No such file or directory
/sbin/ldconfig.real: /usr/lib32/libstdc++-libc6.2-2.so.3 is not a symbolic link

```(I have no idea what those other errors are, or if they are affecting ths install in any way.)

Well, much googling and searching of their forums revealed that apparently, I have to install the 32-bit version of the MySQL client, or something like that.  :/

Can anyone give me a shove onto the right path, here?

---

### Post by rajeev1204 on 2009-09-24
> **Sarteck said:**
> I feel really dumb for asking this, but I've been trying to find out how I can do this all morning.  XP

A bit of background on the problem:
I'm trying to tinker with Sphere Server, a game engine.  In the install process, we are supposed to run, ```
ldd spheresvr
``` and "fix" any libraries that are not found.

```
root@Auron:/usr/lib# ldd /home/sphere/spheresvr
        linux-gate.so.1 =>  (0xf7f2d000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ee8000)
        libmysqlclient.so.15 => not found
        librt.so.1 => /lib32/librt.so.1 (0xf7ede000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7def000)
        libm.so.6 => /lib32/libm.so.6 (0xf7dc9000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7dba000)
        libc.so.6 => /lib32/libc.so.6 (0xf7c57000)
        /lib/ld-linux.so.2 (0xf7f2e000)

```
As you can see, it's not finding my libmysqlclient for some reason.  Odd thing is, I can find it just fine:
```

root@Auron:/usr/lib# ldconfig -v | grep mysql
/sbin/ldconfig.real: Can't stat /usr/lib/kde4/lib: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf95d.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf77cd.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf95cd.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotadad.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib/libplplotf77d.so: No such file or directory
        libmysqlclient.so.16 -> libmysqlclient.so.16.0.0
        libmysqlclient_r.so.15 -> libmysqlclient_r.so.15.0.0
        libmysqlpp.so.3 -> libmysqlpp.so.3.0.0
        libmysqlclient_r.so.16 -> libmysqlclient_r.so.16.0.0
        libmysqlclient.so.15 -> libmysqlclient.so.15.0.0
/sbin/ldconfig.real: Cannot stat /usr/lib32/libmysqlclient_r.so: No such file or directory
/sbin/ldconfig.real: Cannot stat /usr/lib32/libmysqlclient.so: No such file or directory
/sbin/ldconfig.real: /usr/lib32/libstdc++-libc6.2-2.so.3 is not a symbolic link

```(I have no idea what those other errors are, or if they are affecting ths install in any way.)

Well, much googling and searching of their forums revealed that apparently, I have to install the 32-bit version of the MySQL client, or something like that.  :/

Can anyone give me a shove onto the right path, here?


Did you install mysql from add/remove or synaptic?

---

### Post by Sarteck on 2009-09-24
T'was such a long time ago I don't even remember.  Is there a way I can find out?

---

### Post by Sarteck on 2009-09-24
To anyone else having this problem, I solved it by doing the following:

```
sudo getlibs -w http://mirrors.kernel.org/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.75-0ubuntu10_i386.deb
```

**getlibs** (believe it or not XD) gets the libraries needed.  Using the "-w" switch, we can specify a file on the web. :)  I just went to the Packages list and selected i386 instead of amd64.

Yay!

---

