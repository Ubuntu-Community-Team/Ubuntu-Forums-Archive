---
title: "Cannot install zlib1g-dev."
date: 2009-08-09
forum: General Help
---

### Post by pocoman on 2009-08-09
Hi,

I need to install zlib1g-dev. However, I encountered the following error message:

===============
nqc@nqc-laptop:~/setup/openbabel-2.2.0$ sudo apt-get install zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3.3.dfsg-12ubuntu1) but 1:1.2.3.3.dfsg-12ubuntu2 is to be installed
E: Broken packages

==================

Does it mean the newer version of zlib1g installed already? How to roll back the older one?

---

### Post by zvacet on 2009-08-09
```
sudo apt-get -f install
```

---

### Post by pocoman on 2009-08-09
Sorry, it does not work. The same error appears.

---

### Post by andrew.46 on 2009-08-10
Hi pocoman,

I wonder if your sources.list is a little scrambled? Could you post the results of the following:

```
cat /etc/apt/sources.list
```

This will demonstrate the software repositories that you are drawing your downloads from.

Andrew

---

