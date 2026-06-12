---
title: "Ubuntu/RHEL GCC libraries/versions/linking"
date: 2011-08-01
forum: General Help
---

### Post by AbbottSquared on 2011-08-01
My principle machine is Ubuntu 10.10 (x86_64) with gcc version 4.4.5, but I'd like to run the compiled/linked code from it on a RHEL server release 5.4 with gcc version 4.1.2.  

Now, the error at runtime is "version 'GLIBCXX_3.4.9' is not found (required by ./executable)".  The server has /usr/lib64/libstdc++.so.6.0.8, but seems to need at least .so.6.0.9.  However, the admin of the server will not allow the libraries to be updated as "the entire system is tied to an older version of glibc and forcing an  upgrade could break the entire system especially when making the jump  across major revisions."  

He recommended that I build the newer version of glibc in my home directory and link against the libraries, but didn't offer direction on how.  How would I go about doing this?  Would it work?  Is this the best method possible?  I'd greatly appreciate insight into or directions for any solutions to this problem.

---

### Post by karlson on 2011-08-01
> **AbbottSquared said:**
> 
He recommended that I build the newer version of glibc in my home directory and link against the libraries, but didn't offer direction on how.  How would I go about doing this?  Would it work?  Is this the best method possible?  I'd greatly appreciate insight into or directions for any solutions to this problem.

Well that is normal behavior.  There is backward compatibility but not the forward one.

What you should do is install gcc-4.1 if it still available for 10.10.  And use it as a compiler.

The best suggestion though would be to have a build/test machine at the same version as the machine running production.

---

