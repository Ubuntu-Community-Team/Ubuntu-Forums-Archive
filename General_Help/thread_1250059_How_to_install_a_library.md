---
title: "How to install a library?"
date: 2009-08-26
forum: General Help
---

### Post by cpthk on 2009-08-26
I am trying to install some libraries. I do
```

apt-get install libxxxxx

```
And then I locate the library, it's at /usr/lib , but I only see a .gz file under the folder and some useless files. apt-get didn't really unpack and install the library completely. How to install a library and compiled library and header files?

Thanks.

---

### Post by dariyoosh on 2009-08-26
> **cpthk said:**
> I am trying to install some libraries. I do
```

apt-get install libxxxxx

```
And then I locate the library, it's at /usr/lib , but I only see a .gz file under the folder and some useless files. apt-get didn't really unpack and install the library completely. How to install a library and compiled library and header files?

Thanks.


Normally apt-get should install correctly, maybe there is already another version that has not been uninstalled properly. I think there is also a 'remove' option with apt-get. Try to unistall this library and try again.

Otherwise, in the case where the source code is available(often a tar.gz file), well, you can apply the classic method to compile and install it manually.

```

su root
password:
# tar zxvf <compressedfile.tar.gz>
# cd <created directory>
# ./configure
# make
# make install
# make clean

```

But as I said, apt-get should be able to do the job.

Regards,
Dariyoosh

---

### Post by credobyte on 2009-08-26
> **dariyoosh said:**
> 
```

sudo -i
tar zxvf <compressedfile.tar.gz>
cd <created directory>
./configure
make
make install
make clean

```

Fixed for you :KS

---

