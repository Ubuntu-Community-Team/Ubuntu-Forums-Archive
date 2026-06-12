---
title: "Glibc-2.8 or above through synaptic"
date: 2009-11-02
forum: General Help
---

### Post by Vigh on 2009-11-02
Is there a way to install glibc-2.8 or higher through synaptic? If I upgrade ubuntu versions will I be able to install through synaptic. At the moment all I can install is version 2.7

---

### Post by iMisspell on 2009-11-02
Hello again :)

In Ubuntu 9.04, aptitude says...

```

xx@desktop:~$ aptitude search glibc
v   glibc-2.9-1                                                            -                                                                                 
p   glibc-doc                                                              - GNU C Library: Documentation                                                    
v   glibc-doc-reference                                                    -                                                                                 
v   glibc-pic                                                              -                                                                                 
p   glibc-source                                                           - GNU C Library: sources                                                          
xx@desktop:~$
```

---

### Post by 3rdalbum on 2009-11-02
There's the possibility that there might be a PPA for Hardy containing a later glibc; but it wouldn't susprise me if you have to update your distro (everything is built around the distro's version of glibc). New programs tend to support distros up to a year old, and Hardy is now 18 months old.

---

### Post by Vigh on 2009-11-03
upgraded to 9.10 problem solved

---

