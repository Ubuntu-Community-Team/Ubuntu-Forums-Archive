---
title: "Problem with pk12util (and chrome ?)"
date: 2011-06-16
forum: General Help
---

### Post by Werewindlefr on 2011-06-16
Hello Ubuntu users,

I'm using Google Chrome on Ubuntu 11.04 and have been using the nss3 tools for certificate management. Recently, I've had to renew a certificate (an important one that I use for my job), however the browser is supposed to import the private key automatically when the new keys are generated. Unfortunately, because of the way chrome manages certificates, I do not know if the private key was successfully imported (and stored in the nss database). 

I've tried exporting the certificate from the nss database using pk12util, and I get the following errors :

$ pk12util -o cert.pk12 -n NameOfTheCertificate -d sql:$HOME/.pki/nssdb
pk12util: find user certs from nickname failed: Failure to load dynamic library.

Does anyone know what the problem might be, and how to fix it ? I would like to try to recover my certificate before sending an email to the Certificate Authority to get a new one...

---

