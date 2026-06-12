---
title: "p11-kit is causing Stack Overflow"
date: 2012-05-09
forum: General Help
---

### Post by Voluntaryist on 2012-05-09
I have Kubuntu 12.04 64bit. What is p11-kit and why am I getting this error?

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
err:seh:setup_exception_record stack overflow 1808 bytes in thread 0023 eip 7bc3e41f esp 00cb0c20 stack 0xcb0000-0xcb1000-0xeb0000

```

I looked around and [the wine people]("http://forum.winehq.org/viewtopic.php?p=75755&sid=f993ab5fdd5c8c0a3cb0e5ab295c3cb5") say that it is a problem with the 12.04 install. Any help would be greatly appreciated.

---

### Post by Voluntaryist on 2012-05-09
Bump. Anyone have any ideas on this?

---

### Post by amites on 2012-05-10
The Xfce guys seem to have tracked it down to a permissions issue -- I run Gnome-Shell and see the same issue but this might help you out.

[http://laslow.net/2012/05/06/gnome-keyring-issues-in-ubuntu-12-04/](http://laslow.net/2012/05/06/gnome-keyring-issues-in-ubuntu-12-04/)

---

