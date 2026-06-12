---
title: "What's the CA of my certificate!?"
date: 2009-08-11
forum: General Help
---

### Post by DexterLB on 2009-08-11
I created a test certificate with openssl.
```
openssl req -new -x509 -key privkey.pem -out cacert.pem -days 9999
openssl pkcs12 -export -in cacert.pem -inkey privkey.pem -certfile cacert.pem -name "Angel Angelov" -out cert.p12
```
I used it to send a signed e-mail message to myself with evolution, but it says it's not trusted. So, what's the name of the CA (e.g. my CA) that I should trust? There a lot of CAs in the Authority tab but I can't find any non-real CA that's the one I created my certificate with...

---

