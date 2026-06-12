---
title: "Is Aptitude natively part of Ubuntu, or is it a 3rd party program that is installed?"
date: 2012-06-03
forum: General Help
---

### Post by charleswb on 2012-06-03
Is Aptitude natively installed on stock Ubuntu, or is it a 3rd party program add on that people install?

I had thought that Aptitude was a 3rd party program that people install, but someone told me it's in Man and to read Man Aptitude. That suggests to me that Aptitude is natively part of Ubuntu.

I have been learning Apt-Get, but haven't yet got to learning Aptitude. I don't think I have Aptitude installed.

When I typed Man Aptitude it says:
No manual entry for aptitude

---

### Post by westie457 on 2012-06-03
Hi aptitude is not installed.```
sudo apt-get install aptitude
``` will install it then the man page will be available.

AFAIK apt is a variation of aptitude, they work the same with some small differences.

---

### Post by ajgreeny on 2012-06-03
All of the "apt" group of applications and utilities, apt-get, synaptic, aptitude, and maybe more that I can not think of at the moment are ways of using dpkg, which actually does the package management.

I seem to remember that in the past aptitude was a default app of ubuntu, but I may be mistaken.  Personally, I never saw a reason to use it, so stuck with apt-get, or mostly, synaptic, the best of all the applications available in my experience and opinion.

---

### Post by PaulW2U on 2012-06-03
> **ajgreeny said:**
> I seem to remember that in the past aptitude was a default app of ubuntu, but I may be mistaken.

That's correct, it was. I think it was removed from being a default application in either 10.10 or 11.04.

I've always used it although some seem not to trust it at all and will do everything they can to advise against using it. :confused:

---

### Post by forrestcupp on 2012-06-03
A long, long time ago, Aptitude was better at handling certain things than apt-get, and it was recommended to use over apt-get. But that was a long time ago.

Since then, some functionality has been added to apt-get that makes it the preferable method. If you're sticking with Ubuntu, there's now no reason at all to use Aptitude, unless it's just something you have always used and liked.

---

