---
title: "Library corruption on crunchbang"
date: 2011-04-12
forum: General Help
---

### Post by moz@n on 2011-04-12
Hi, yesterday i tried to upgrade my system because i got internet, so when i run apt-get , at the end, when ldconfig starts, there was some errors on libraries, and then all the system crashes.

So, I boot from another Crunchbang DVD and I run cp /lib/*, to "restore" the libraries on my system.
Fortunately, there were no errores...But now when I run apt-get and he tries to reinstall the "true" libraries, it do the same error when running ldconfig...

Now some program crashes, as irssi, and I decided to install it from source... When I run configure, there was some errors:

```
*** 'pkg-config --modversion glib-2.0' returned 2.18.2, but GLIB (2.24.2) *** was found! If pkg-config was correct, then it is best *** to remove the old version of GLib. You may also be able to fix the error *** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing *** /etc/ld.so.conf. Make sure you have run ldconfig if that is *** required on your system. *** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH *** to point to the correct configuration files no
```I think this is because the libraries are not the same...( in my Crunchbang DVD, and my system )

So I tried to lunch "ldconfig" and then all the programs crashes with SIGSEGV... and when I run pkg-config I had this:

```
pkg-config: /lib/libc.so.6: version `GLIBC_2.9' not found (required by /lib/libglib-2.0.so.0)
```So, there are some way to repair? 

Thank, and sorry for my very bad english ;)

---

