---
title: "Getting kde on ubuntu 10.04"
date: 2011-11-16
forum: General Help
---

### Post by snakehorse on 2011-11-16
Hi,

            I tried to install KUBUNTU Desktop on Ubuntu but got the following prompt:

> Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore, there could be a conflict between software packages which are not allowed to be installed at the same time.



Regards.

---

### Post by jjex22 on 2011-11-16
I think this should help you:

[KDE..Buntu!]("http://www.psychocats.net/ubuntu/kde")

hope it helps!

---

### Post by snakehorse on 2011-11-16
Did exactly the same bro.

---

### Post by raja.genupula on 2011-11-16
hi open your terminal and 
```
sudo apt-get install -f 
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

do them !


all the best man.

---

### Post by snakehorse on 2011-11-16
Hi,

Done it in terminal. got below trace..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
E: Broken packages

---

### Post by tartalo on 2011-11-16
It might help:
[http://ubuntuforums.org/showpost.php?p=5962046&postcount=9](http://ubuntuforums.org/showpost.php?p=5962046&postcount=9)

---

### Post by raja.genupula on 2011-11-16
could try this please 

```
 sudo aptitude install kubuntu-desktop
```

---

### Post by snakehorse on 2011-11-16
Tried first time to resolve and got it. marked for removal the 'culprit' package in synaptic manager and got it fixed. Thanks all for pointers.

---

### Post by mastablasta on 2011-11-16
i just wanted to give you this same advice  :-)
 
anyway now that you installed it you should knwo that KDE in 10.04 had quite a few issues remianing (bugs that were very annoying). many were resolved in one later version. so if you plan to stay with it you could upgrade the KDE via PPA.
 
i installed 10.10 a tthe time because it supported my sound better. but i found a few issues with KDE . upgrading only KDE via PPA resolved them.

---

