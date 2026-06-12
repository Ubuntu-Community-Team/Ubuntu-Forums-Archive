---
title: "ubuntu breazy and fuseftp"
date: 2006-05-05
forum: General Help
---

### Post by deeeed on 2006-05-05
Hi,
I would like to "mount" an ftp connexion in a /mnt/ftp so found that i had to install fuseftp so I tried to install fuseftp on my breezy installation but I have lots of problems i can't solve alone ;s
First of all i tried to get the package from apt but it didn't find it..
root@clara: ~# apt-cache search fuseftp
root@clara:~# 

Then i looked for another way to get .deb files so downloaded the .deb from [http://debian.jox.be/](http://debian.jox.be/) but here i got errors too.

My last try was to install Fuse.pm with the perl CPAN module but it doesn't compil..
root@clara:~# perl -MCPAN -e "install Fuse"
...
Fuse.xs:777: warning: (near initialization for 'fops')
Fuse.xs:777: warning: excess elements in struct initializer
Fuse.xs:777: warning: (near initialization for 'fops')
Fuse.xs:777: warning: excess elements in struct initializer
Fuse.xs:777: warning: (near initialization for 'fops')
Fuse.xs:777: warning: excess elements in struct initializer
Fuse.xs:777: warning: (near initialization for 'fops')
Fuse.xs:777: warning: excess elements in struct initializer
Fuse.xs:777: warning: (near initialization for 'fops')
Fuse.xs:777: warning: excess elements in struct initializer
Fuse.xs:777: warning: (near initialization for 'fops')
Fuse.xs:777: error: storage size of 'fops' isn't known
make: *** [Fuse.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
root@clara:~#

I hope you have an idea..

Sorry for my english which is not correct..

---

