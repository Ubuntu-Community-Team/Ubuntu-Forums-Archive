---
title: "problem with ssh and libcrypto"
date: 2012-05-16
forum: General Help
---

### Post by ammadeus on 2012-05-16
Hello all,

I have a huge problem that I'm unable to run ssh on ubuntu 10.04 LTS

when attempting to run ssh I get an error

```
ssh: relocation error: ssh: symbol EVP_CIPHER_CTX_get_app_data, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```
running locate libcrypto.so.0.9.8 produces
```
/home/nao/programs/urbi-sdk-2.7.1-linux-x86_64-gcc4/lib/libcrypto.so.0.9.8
/lib/libcrypto.so.0.9.8
/lib32/libcrypto.so.0.9.8
/lib32/i486/libcrypto.so.0.9.8
/lib32/i586/libcrypto.so.0.9.8
/lib32/i686/cmov/libcrypto.so.0.9.8
/usr/lib/libcrypto.so.0.9.8
/usr/lib32/libcrypto.so.0.9.8
/usr/local/urbi/lib/libcrypto.so.0.9.8

```Which libcrypto does ssh look for? how can i find this

please help me, this is very urgent

thanks in advance

---

### Post by cong06 on 2012-06-11
If you haven't solved this already, try moving or deleting the file:
```

/home/nao/programs/urbi-sdk-2.7.1-linux-x86_64-gcc4/lib/libcrypto.so.0.9.8

```

If that doesn't fix it, I just had this problem also, so I was forced to download and then reinstall the package:
```

sudo aptitude download libssl0.9.8
sudo dpkg -i libssl0.9.8_0.9.8*.deb

```

I may run fsck just to make sure I didn't have some kind of file system corruption.

---

