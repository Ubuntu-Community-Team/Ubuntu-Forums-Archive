---
title: "QTparted installation error"
date: 2005-02-19
forum: General Help
---

### Post by cutOff on 2005-02-19
Hi

I'm trying to install QTparted but apt-get gives me this error

> Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtparted: Depends: libparted1.6-0 (>= 1.6.0) but it is not installable
E: Broken packages
and when i do
> cutoff@this:~$ sudo apt-get install libparted
Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting libparted1.6-12 instead of libparted
libparted1.6-12 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Does anybody knows to solve this prob?

Thanx

PD I'm using Hoary

---

### Post by cutOff on 2005-02-20
Solved   :grin: 

I've changed Hoary repos to Warty and it has installed nice.



Cheers!

---

