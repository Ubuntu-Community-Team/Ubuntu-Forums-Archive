---
title: "Encryption Software for Ubuntu"
date: 2010-08-09
forum: General Help
---

### Post by TomAbada on 2010-08-09
hi all
i need a good encryption software 
prefer without desktop environment 
cuz im gonna use it by command line

if someone knows a good software it will help me a lot

---

### Post by YesWeCan on 2010-08-09
see 'man openssl'

example:
openssl aes-128-cbc -salt -in file -out file.aes

---

### Post by aeiah on 2010-08-09
what do you want to encrypt and what is the purpose? if you want it to be portable you may want truecrypt, or if you want to encrypt specific files instead of virtual columes you may want openssl, or gnupg etc

---

### Post by TomAbada on 2010-08-09
i want to encrypt specific files
prefer using a code than a key

---

### Post by jimmah6786 on 2010-08-09
I use ccrypt, can be installed via apt-get.

Cheers,

Jim

---

