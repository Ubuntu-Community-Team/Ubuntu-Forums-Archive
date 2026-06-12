---
title: "problems with libaries"
date: 2005-02-15
forum: General Help
---

### Post by dott.malcom on 2005-02-15
Hi all,
I'm trying to install the VPNC client to get my linuxbox connected with vpn netowrk of my university, so the program is this [http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/) 

So i've also installed this libraries
[ftp://ftp.gnupg.org/gcrypt/libgcrypt/libgcrypt-1.2.0.tar.gz](ftp://ftp.gnupg.org/gcrypt/libgcrypt/libgcrypt-1.2.0.tar.gz) 
[ftp://ftp.gnupg.org/gcrypt/alpha/libgpg-error/libgpg-error-0.7.tar.gz](ftp://ftp.gnupg.org/gcrypt/alpha/libgpg-error/libgpg-error-0.7.tar.gz) 
[http://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.2-rm+zomb.1.tar.gz](http://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.2-rm+zomb.1.tar.gz) 
because the installation guide says that are required; the installation procedure is as always[B]
./configure
make 
make install[/B]
but after this procedure i try to run **vpnc**  and i get a message that says 
*cannot find libcrypt.so .......* 
this file is in the /usr/lib dir, why linux doesn't find it if is in the same dir as the other library files?

Do anybody know other program that can handle vpn connection?
thanks in advance

---

