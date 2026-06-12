---
title: "openssl ca -config"
date: 2010-10-19
forum: General Help
---

### Post by technicallygeek on 2010-10-19
issues with generating a Cert Signing Request, I have the .csr when i try to sign new with CA ```
 sudo openssl ca -in server.csr -config /etc/ssl/openssl_cnf 
```

 
Am I missing some commands for -config?

---

### Post by Astrofly on 2010-10-19
Try this. 
you misspelled openssl.cnf - openssl_cnf

Code:
 sudo openssl ca -in server.csr -config /etc/ssl/openssl.cnf

---

