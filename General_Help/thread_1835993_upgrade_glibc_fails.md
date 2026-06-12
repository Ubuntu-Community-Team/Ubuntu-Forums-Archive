---
title: "upgrade glibc fails"
date: 2011-08-30
forum: General Help
---

### Post by mhart on 2011-08-30
Hai,

Iam installing android SDK and it requires me to update to glibc 2.7.

However when tried it failed.


sudo apt-get upgrade glibc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 

dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libc6          2.12.1-0ubuntu Embedded GNU C Library: Shared libraries

---

### Post by mhart on 2011-09-02
Using: Ubuntu 10.10

Anybody got any idea?

---

### Post by raja.genupula on 2011-09-02
search for that one in synaptic package manager

---

### Post by ivotkl on 2012-12-10
Hi, I'm having a similar problem. I need to upgrade glibc to 2.2 or 2.3. However, I cannot upgrade it on terminal and latest version showing on synaptic is 2.15.

I need it to try ATI proprietary drivers.

My OS is:
```
Linux ivan-desktop 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:49:02 UTC 2012 i686 athlon i386 GNU/Linux
```

---

### Post by andrea_m2 on 2013-09-10
I was also trying to upgrade to 2.7 (from 2.18) without success, then I looked for the release dates of glibc and found out that 2.7 is older than 2.18, that's why it does not upgrade [https://sourceware.org/glibc/wiki/Glibc%20Timeline](https://sourceware.org/glibc/wiki/Glibc%20Timeline)
Is it correct?

---

