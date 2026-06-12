---
title: "Unmet dependencies for libc6"
date: 2012-03-25
forum: General Help
---

### Post by huashi on 2012-03-25
My system: 

uname -a
Linux shilap 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

sudo apt-get upgrade

Reading package lists... 8%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5)
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5)
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
E: Unmet dependencies. Try using -f.

I think the problem started when I tried to install Android SDK (not 100% sure). But now it blocks me of installing any new packages.

Having tried many options to solve this issue but with no luck. Anybody help me out here?

---

