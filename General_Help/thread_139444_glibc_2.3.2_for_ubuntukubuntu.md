---
title: "glibc 2.3.2 for ubuntu/kubuntu"
date: 2006-03-04
forum: General Help
---

### Post by emreakbas on 2006-03-04
Can I find  the library file (libc.so.6) of glibc-2.3.2 (archtitecture is  i386) for ubuntu/kubuntu? 

This is required for me to run MABTLAB R7.1 R14SP3 on my kubuntu. When I start MATLAB I get the error described in the following thread: 

[http://ubuntuforums.org/showthread.php?t=135135](http://ubuntuforums.org/showthread.php?t=135135)

Does anyone get the same error?  

After communicating with the MATLAB Support Center, they finally concluded that the error is due to the glibc version. MATLAB 7.1 R14SP3  requires glibc-2.3.2.  Now I should compile glibc-2.3.2, but before doing it, I wanted to ask for a ready-built libc.so.6 for i386. 

Thanks for all in advance.

---

### Post by hw-tph on 2006-03-04
Downgrading to 2.3.2 is likely to break your entire system so I wouldn't recommend it. 2.3.2 is pretty old by now and you should push them for a new revision that can use current GNU libc versions (Ubuntu 5.10 comes with GNU libc 2.3.5).


Håkan

---

### Post by emreakbas on 2006-03-04
No no, I don't want to downgrade my system. I only want the file  libc.so.6   of glibc-2.3.2.   I will put this file under the appropriate directory  of MATLAB and hope it would solve my problem. 

How can I find this file? Is "compiling" the only way?

---

### Post by hw-tph on 2006-03-04
It depends on how the Matlab creators have implemented their dependancies on shared libraries, but unlike in Windows the default behaviour is *not* to look in the same directory as the executable for libraries. Most Linux applications instead depend on ldconfig to find out what libraries are available and what functionality they provide.

You could grab the Debian package of GNU libc 2.3.2 from [the temporary Debian packages mirror](http://pdo.debian.net).

---

