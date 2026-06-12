---
title: "Package 'libssl' has no installation candidate"
date: 2012-05-13
forum: General Help
---

### Post by Noob_Zaiboot on 2012-05-13
Hi all,

I'm trying to install tor software from source. Everytime i run configure i get this warning:

```
checking for openssl directory... configure: WARNING: Could not find a linkable openssl.  If you have it installed somewhere unusual, you can specify an explicit path using --with-openssl-dir
configure: WARNING: On Debian, you can install openssl using "apt-get install libssl"
configure: WARNING:    You will probably need libssl-dev too.
configure: error: Missing libraries; unable to proceed.
```when i run "apt-get install libssl" this comes up:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libssl' has no installation candidate
```I've searched google and found nothing. Can anybody help me?

btw im running ubuntu 12.04 LTS Precise Pangolin

Thanks in advance

---

### Post by rai4shu2 on 2012-05-13
Because you're compiling, you need to install libssl-dev. That should get you past that particular error.

---

### Post by Noob_Zaiboot on 2012-05-13
Thank You. That worked.

---

