---
title: "How to list 32 bit apps in use on 64 bit machine"
date: 2010-09-19
forum: General Help
---

### Post by zak_neutron on 2010-09-19
Hi in light of the current kernel flaw being circulated:

[http://www.h-online.com/security/news/item/Hole-in-Linux-kernel-provides-root-rights-1081317.html](http://www.h-online.com/security/news/item/Hole-in-Linux-kernel-provides-root-rights-1081317.html)

and the solution being proposed here:

[http://seclists.org/fulldisclosure/2010/Sep/273](http://seclists.org/fulldisclosure/2010/Sep/273)

How do I know if I have any 32 bit binaries running on my machine:

Ubuntu: 10.04 64 bit

I generally always install most of my apps through the repo's but I **may** have installed some apps from source code or other methods. So how can I list any 32 bit binaries running on my machine before implementing the solution cited in the second link?

Thanks

---

### Post by Vaphell on 2010-09-19
maybe this would do?
```
find /usr/bin -type f -exec file {} \;| grep 32-bit
```
in my case it returns few wine related binaries

no idea how to check running apps though, maybe ps and testing each one with file command?

---

### Post by zak_neutron on 2010-09-19
Thanks Vaphell - worked a treat! :)

---

