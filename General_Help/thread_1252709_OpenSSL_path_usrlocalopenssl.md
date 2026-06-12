---
title: "OpenSSL path /usr/local/openssl"
date: 2009-08-29
forum: General Help
---

### Post by you-bunt-too? on 2009-08-29
I'm very new...

Running 9.04 Ubuntu Server. I installed Openssl 0.9.8k manually.  Now when I run apt-get, I have unmet dependencies.  One of them is OpenSSL.  

When I install bind9.5 manually, I specified the openssl path as /usr/local/openssl.

What do you recommend I do to clean this up? ;)

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ca-certificates gnupg libcurl3-gnutls libgpgme11 openssl
Suggested packages:
  gnupg-doc xloadimage imagemagick eog gpgsm openssl-doc
The following NEW packages will be installed:
  ca-certificates gnupg libcurl3-gnutls libgpgme11 openssl
0 upgraded, 5 newly installed, 0 to remove and 48 not upgraded.
Need to get 0B/1928kB of archives.
After this operation, 7639kB of additional disk space will be used.

/usr/local/openssl$ ls -al
total 48
drwxr-xr-x  9 root root 4096 2009-08-24 13:06 .
drwxr-xr-x 11 root root 4096 2009-08-24 13:04 ..
drwxr-xr-x  2 root root 4096 2009-08-24 13:06 bin
drwxr-xr-x  2 root root 4096 2009-08-24 13:06 certs
drwxr-xr-x  3 root root 4096 2009-08-24 13:06 include
drwxr-xr-x  4 root root 4096 2009-08-24 13:06 lib
drwxr-xr-x  6 root root 4096 2009-08-24 13:04 man
drwxr-xr-x  2 root root 4096 2009-08-24 13:06 misc
-rw-r--r--  1 root root 9374 2009-08-24 13:06 openssl.cnf
drwxr-xr-x  2 root root 4096 2009-08-24 13:06 private

---

