---
title: "password file location??"
date: 2010-12-19
forum: General Help
---

### Post by Praveen30 on 2010-12-19
hi friends,

i just want to know where the password(login) file is located in ubuntu 9.10 and what is the encryption method(md5 etc..) for encrypting these passwords??

---

### Post by noah++ on 2010-12-19
Passwords in **/etc/shadow** are SHA512 hashes.

_References:_
[http://linux.die.net/man/5/shadow](http://linux.die.net/man/5/shadow)
[http://jonmccune.wordpress.com/2009/07/28/1-vs-6-in-etcshadow/](http://jonmccune.wordpress.com/2009/07/28/1-vs-6-in-etcshadow/)

---

