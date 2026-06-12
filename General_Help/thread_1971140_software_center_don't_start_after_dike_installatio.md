---
title: "software center don't start after dike installation"
date: 2012-05-02
forum: General Help
---

### Post by marvinuntu on 2012-05-02
1-dike is no  more presente in ubuntu software center;

2-i download it from 
[https://www.firma.infocert.it/software/dike-4.2.9-i386.deb](https://www.firma.infocert.it/software/dike-4.2.9-i386.deb)

3-i install it with command "dpkg -e dike-4.2.9-i386.deb"

4-software-center no more start
---
marvin@marvin:~$ software-center
/usr/bin/python: /usr/share/dike/lib/libcrypto.so.1.0.0: no version information available (required by /usr/bin/python)
/usr/bin/python: /usr/share/dike/lib/libcrypto.so.1.0.0: no version information available (required by /lib/i386-linux-gnu/libssl.so.1.0.0)
/usr/bin/python: /usr/share/dike/lib/libcrypto.so.1.0.0: no version information available (required by /lib/i386-linux-gnu/libssl.so.1.0.0)
/usr/bin/python: relocation error: /lib/i386-linux-gnu/libssl.so.1.0.0: symbol EVP_aes_128_gcm, version OPENSSL_1.0.1 not defined in file libcrypto.so.1.0.0 with link time reference
---

5-i uninstall dike with command "dpkg -r dike"

6-software center now start

anyone have notice of this problem?
thanks
marvin

---

