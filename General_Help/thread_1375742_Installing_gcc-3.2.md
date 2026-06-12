---
title: "Installing gcc-3.2"
date: 2010-01-08
forum: General Help
---

### Post by SalsaBr on 2010-01-08
Hi, 

 is it possible, and if so, how do I install gcc-3.2? I have a server running Red Hat 3, and when I try to run one of my applications in it, the server complains about not having GLIBC 3.2.4. I tried to install it, but there were some conflicts, so I decided to install gcc-3.2 to recompile my app.
  I tried to convert a rpm package to deb, but got this error when I tried to install it:

Unpacking gcc-c++ (from ./gcc-c++_3.2.3-20_i386.deb) ...
dpkg: error processing ./gcc-c++_3.2.3-20_i386.deb (--install):
 trying to overwrite `/usr/share/man/man1/g++.1.gz', which is also in package g++
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 ./gcc-c++_3.2.3-20_i386.deb

  I'm currently using ubuntu 9.04 on my development server.

---

### Post by sanderd17 on 2010-01-08
can you use this thread?

[http://ubuntuforums.org/showthread.php?t=395631]("http://ubuntuforums.org/showthread.php?t=395631")

---

### Post by sanderd17 on 2010-01-08
> GCC 3.2.3 Setup (only for older kits)
For older kits, it is necessary to install the gcc 3.2.3 compiler which is not available in newer Ubuntu repositories. However, it can be installed via pacman:
```
mkdir $ATHENAKITDIR/gcc323
cd $ATHENAKITDIR/gcc323
source /afs/cern.ch/atlas/software/pacman/pacman-latest/setup.sh
pacman -pretend-platform SLC-3 -allow trust-all-caches -get http://classis01.roma1.infn.it/pacman/cache:gcc323-slc3
```
gcc 3.2.3 can now be set up with source ```
$ATHENAKITDIR/gcc323/setup.sh
```.
found the previous at [https://twiki.cern.ch/twiki/bin/view/Atlas/DistKitOnUbuntu#GCC_3_2_3_Setup_only_for_older_k]("https://twiki.cern.ch/twiki/bin/view/Atlas/DistKitOnUbuntu#GCC_3_2_3_Setup_only_for_older_k")
hope it helps

---

### Post by SalsaBr on 2010-01-08
> **sanderd17 said:**
> can you use this thread?

[http://ubuntuforums.org/showthread.php?t=395631]("http://ubuntuforums.org/showthread.php?t=395631")


   No, that doesn't help. He installed gcc-3.4. I need 3.2, which is not a debian package, or at least that's what I think.

---

### Post by SalsaBr on 2010-01-08
> **sanderd17 said:**
> found the previous at [https://twiki.cern.ch/twiki/bin/view/Atlas/DistKitOnUbuntu#GCC_3_2_3_Setup_only_for_older_k]("https://twiki.cern.ch/twiki/bin/view/Atlas/DistKitOnUbuntu#GCC_3_2_3_Setup_only_for_older_k")
hope it helps

  I'll try this one and let you know later. Thanks.

---

