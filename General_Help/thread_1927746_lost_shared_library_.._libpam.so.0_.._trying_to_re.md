---
title: "lost shared library .. libpam.so.0 .. trying to repair from Live CD"
date: 2012-02-18
forum: General Help
---

### Post by dragonfly41 on 2012-02-18
I've been trying to recover a ubuntu 10.10 configuration ..
after running e2fsck

I can now boot up but ubuntu goes into tty1 console mode and not to desktop

when I try to logon I have the message .....

```
/bin/logon: error while loading shared libraries libpam.so.0
cannot open shared object file
no such file or directory
```so I booted up ubuntu Live CD (solved an earlier problem when Try Ubuntu would not click through) and I checked the location of libpam.so.0 file in the Live CD root .. 

```
locate libpam.so
/lib/libpam.so.0
/lib/libpam.so.0.82.2
```
I then looked for same file location in the mounted internal ubuntu root partition which is not starting up ..

there is no sign of libpam.so.0 .. which is consistent with the login error

Any reasons why I might lose a shared library  ??

To avoid a ubuntu reinstallation/repair .. can I try I copying the shared library from the Live CD /lib/ folder into the internal ubuntu root folder?

How do I copy shared library from Ubuntu Live CD file system into /dev/sda7  .. /lib folder     (root partition)?

At first attempt I'm getting permissions problems when I try that using Nautilus.

Root partition (/dev/sda7) is mounted on /media/8eeb2f0d-92c7-463e-8961-3a1241fc148a

....

Or should I just try to repair the corrupt root and home partitions?

....

---

### Post by gopukrishnantec on 2012-10-10
Anyone knows the solution for the above problem ?????

---

