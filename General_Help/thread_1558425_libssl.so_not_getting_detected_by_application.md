---
title: "libssl.so not getting detected by application"
date: 2010-08-22
forum: General Help
---

### Post by MASTERofMINDS on 2010-08-22
I'm using 64 bit version of Ubuntu 10.04 and since I was unable to post in the x84_64 forum I'm posting in this forum.

I'm getting this error...

```
muneeb@muneeb-desktop:/usr/lib$ sifyconnect 
sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

```

I've installed openssl and also done symlinking already.


```
apt-cache policy  libssl-dev
libssl-dev:
  Installed: 0.9.8k-7ubuntu8
  Candidate: 0.9.8k-7ubuntu8
  Version table:
 *** 0.9.8k-7ubuntu8 0
        500 http://in.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
```

Check the symlinking...

```
muneeb@muneeb-desktop:/usr/lib$ ls -l libssl*
-rw-r--r-- 1 root root 226040 2010-04-11 03:02 libssl3.so
lrwxrwxrwx 1 root root     10 2010-08-21 08:19 libssl3.so.1d -> libssl3.so
-rw-r--r-- 1 root root 554638 2010-03-30 23:41 libssl.a
lrwxrwxrwx 1 root root     20 2010-08-22 17:05 libssl.so -> /lib/libssl.so.0.9.8
lrwxrwxrwx 1 root root     20 2010-08-21 08:19 libssl.so.0.9.8 -> /lib/libssl.so.0.9.8
lrwxrwxrwx 1 root root     20 2010-08-22 17:31 libssl.so.4 -> /lib/libssl.so.0.9.8
```

The application also requires libcrypto.so.4 which I have already installed...

```
muneeb@muneeb-desktop:/usr/lib$ ls -l libcryp*
-rw-r--r-- 1 root root   76244 2010-05-21 14:37 libcrypt.a
-rw-r--r-- 1 root root 3450360 2010-03-30 23:41 libcrypto.a
lrwxrwxrwx 1 root root      16 2010-08-21 08:18 libcryptopp.so.8 -> libcrypto++.so.8
lrwxrwxrwx 1 root root      23 2010-08-22 17:05 libcrypto.so -> /lib/libcrypto.so.0.9.8
lrwxrwxrwx 1 root root      23 2010-08-21 08:18 libcrypto.so.0.9.8 -> /lib/libcrypto.so.0.9.8
lrwxrwxrwx 1 root root      23 2010-08-22 17:31 libcrypto.so.4 -> /lib/libcrypto.so.0.9.8
lrwxrwxrwx 1 root root      20 2010-08-21 08:18 libcrypto++.so.8 -> libcrypto++.so.8.0.0
-rw-r--r-- 1 root root 4946936 2009-11-07 20:22 libcrypto++.so.8.0.0
lrwxrwxrwx 1 root root      18 2010-08-21 08:18 libcrypt.so -> /lib/libcrypt.so.1
lrwxrwxrwx 1 root root      19 2010-08-21 08:18 libcryptui.so.0 -> libcryptui.so.0.0.0
-rw-r--r-- 1 root root   73312 2010-04-09 16:19 libcryptui.so.0.0.0

```

I was using this application on Ubuntu 10.04 32 bit... It worked before on 32 bit with these settings but now it's not working on 64 bit...

---

