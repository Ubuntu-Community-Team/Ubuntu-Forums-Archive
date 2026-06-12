---
title: "Have gcc 4.2.4, need 4.2.3"
date: 2011-02-16
forum: General Help
---

### Post by ufuser01 on 2011-02-16
Hi,

I am using Matlab on Ubuntu for MEX. MEX uses gcc 4.2.3 and when I type "gcc -v", I get the output below. Synaptic package manager shows that gcc 4.2.3 and 4.2.4 are selected and installed. How to make sure that I have only gcc 4.2.3? Marking 4.2.4 for uninstall selects 4.2.3 too, so I don't want to do that. 

# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)


Thanks.

---

### Post by anglican on 2011-02-16
> **ufuser01 said:**
> Hi,

I am using Matlab on Ubuntu for MEX. MEX uses gcc 4.2.3 and when I type "gcc -v", I get the output below. Synaptic package manager shows that gcc 4.2.3 and 4.2.4 are selected and installed. How to make sure that I have only gcc 4.2.3? Marking 4.2.4 for uninstall selects 4.2.3 too, so I don't want to do that. 

# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)


Thanks./usr/bin/gcc is a link to /usr/bin/gcc-4.4. If you have other versions of gcc installed (I have gcc-4.1) you can simply change the link to point to that instead:
```
cd /usr/bin
sudo unlink gcc
sudo ln -s gcc-4.1 gcc
```

H

---

