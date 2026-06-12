---
title: "Evince 2.22.2 on 8.04 needs to be upgraded"
date: 2009-08-26
forum: General Help
---

### Post by afrodeity on 2009-08-26
Evince 2.22.2 on Ubuntu 8.04 is not opening latest Adobe PDFs which require a newer version. Where is the upgrade or support?

```

To view the full contents of this document, you need a later version of the PDF viewer. You can upgrade
to the latest version of Adobe Reader from www.adobe.com/products/acrobat/readstep2.html
For further support, go to www.adobe.com/support/products/acrreader.html

```

---

### Post by credobyte on 2009-08-26
Open Add/Remove and install Adobe Reader ? :-s

---

### Post by afrodeity on 2009-08-26
It's a 60mb download of a proprietory piece of software which defeats the whole purpose of FOSS, might not work on 64bit Ubuntu, but thanks anyway.

---

### Post by credobyte on 2009-08-26
> **afrodeity said:**
> It's a 60mb download of a proprietory piece of software which defeats the whole purpose of FOSS, might not work on 64bit Ubuntu, but thanks anyway.

64bit version from Mediabuntu works just fine :)

---

### Post by afrodeity on 2009-08-27
medibuntu repo is selected but

```
 sudo apt-get install acroread
[sudo] password for afrodeity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

```

Therefore no acroread in 8.04 medibuntu? I was referred to canonical third party repo, but also nothing, please help.

---

### Post by afrodeity on 2009-08-27
medibuntu repo is selected but

```
 sudo apt-get install acroread
[sudo] password for afrodeity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

```

Therefore no acroread in 8.04 medibuntu? I was referred to canonical third party repo, but also nothing, please help.

---

### Post by credobyte on 2009-08-27
Ah, my mistake - forgot about the fact that you are on 8.04. Mediabuntu doesn't offer acroread for Hardy ( [http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html) ) :(

---

### Post by afrodeity on 2009-08-28
It's supposed to be LTS ie Long Term Support!!! Evince should therefore be upgraded in the repo and support for latest adobe reader surely? I guess I should upgrade, but am waiting for Karma which is supposed to be next LTS.

---

