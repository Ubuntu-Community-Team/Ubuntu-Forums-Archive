---
title: "Evolution not working after 9.10 upgrade"
date: 2009-10-20
forum: General Help
---

### Post by bodam on 2009-10-20
Just upgraded my laptop to 9.10 and almost everything came over flawlessly, except, Evolution.  It does not appear to be installed so I did the following and got the following error.  Any ideas?

bodam@londom-laptop:~$ sudo apt-get install evolution
[sudo] password for londom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution: Depends: evolution-common (= 2.28.0-0ubuntu4) but 2.28.1-0ubuntu1 is to be installed
             Recommends: evolution-documentation (= 2.28.0-0ubuntu4) or
                         evolution-documentation-en (= 2.28.0-0ubuntu4) but 2.28.1-0ubuntu1 is to be installed
E: Broken packages

---

