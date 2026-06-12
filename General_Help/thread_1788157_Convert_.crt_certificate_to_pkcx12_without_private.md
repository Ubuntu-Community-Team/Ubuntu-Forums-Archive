---
title: "Convert .crt certificate to pkcx12 without private key"
date: 2011-06-22
forum: General Help
---

### Post by ocwo92 on 2011-06-22
I have a personal certificate in a binary .crt format that can be imported in Windows for signing email. However, I need to import it into Evolution, and it doesn't seem to recognize the format.

For various reasons(*) I don't have the private key for my certificate. Otherwise I could probably convert it to PKCS12 via:

```
openssl pkcs12 -export -out mycert.p12 -inkey mycert.key -in mycert.crt
```
How do I convert the .crt file to at PKCS12 file that Evolution will import when I don't have the private key?

(*) For political reasons, my country has a central agency that has taken upon itself to issue certificates while issuing and storing the private keys in a single point of failure rather than letting each individual own his or her key, and it doesn't send the private keys to their owners. This is of course fundamentally flawed, but I can't change that. Please don't suggest that I create my own certificate, as I know how to do that--for example, I have a CAcert certificate already.)

---

