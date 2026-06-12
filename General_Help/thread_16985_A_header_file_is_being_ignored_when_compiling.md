---
title: "A header file is being ignored when compiling"
date: 2005-02-25
forum: General Help
---

### Post by CGameProgrammer on 2005-02-25
I'm trying to install OpenVPN, which requires OpenSSL. I installed that as well, and "config/make/make install"ed OpenSSL without a problem. However, OpenVPN's configure script still says it can't find it:

configure: checking for OpenSSL Crypto Library and Header files...
checking openssl/evp.h usability... no
checking openssl/evp.h presence... no
checking for openssl/evp.h... no
configure: error: OpenSSL Crypto headers not found.

So I did a "find /usr -name evp.h" and got:
/usr/local/ssl/include/openssl/evp.h
/usr/openssl-0.9.7e/crypto/evp/evp.h
/usr/openssl-0.9.7e/include/openssl/evp.h

The first path is probably the one it should be finding, but it isn't. What do I do? Do I have to set some parameter somewhere to indicate that /usr/local/ssl/include is an include path that gcc should look for?

---

### Post by rock freak on 2006-03-14
hey there i ahve the same problem did you ever sort this out????

---

