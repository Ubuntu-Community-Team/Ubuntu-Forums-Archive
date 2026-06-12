---
title: "getting the following error Installing Gyachi***help***"
date: 2010-03-24
forum: General Help
---

### Post by Apoorvbarwa on 2010-03-24
Hi,
I am using ubuntu 9.10, while intalling gyachi i get following make error.Can anyone tell me how to fix this.

make[1]: Leaving directory `/media/f585f0e0-1605-4ee2-8bbc-bfe7af23fa05/gyachi-1.1.71/po'
Making install in lib
make[1]: Entering directory `/media/f585f0e0-1605-4ee2-8bbc-bfe7af23fa05/gyachi-1.1.71/lib'
make[2]: Entering directory `/media/f585f0e0-1605-4ee2-8bbc-bfe7af23fa05/gyachi-1.1.71/lib'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libgyachi.la' '/usr/local/lib/libgyachi.la'
libtool: install: /usr/bin/install -c .libs/libgyachi.so /usr/local/lib/libgyachi.so
/usr/bin/install: cannot create regular file `/usr/local/lib/libgyachi.so': Permission denied
make[2]: *** [install-gyachilibLTLIBRARIES] Error 1
make[2]: Leaving directory `/media/f585f0e0-1605-4ee2-8bbc-bfe7af23fa05/gyachi-1.1.71/lib'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/media/f585f0e0-1605-4ee2-8bbc-bfe7af23fa05/gyachi-1.1.71/lib'
make: *** [install-recursive] Error 1

---

