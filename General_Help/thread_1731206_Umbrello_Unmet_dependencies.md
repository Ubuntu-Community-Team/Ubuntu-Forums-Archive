---
title: "Umbrello: Unmet dependencies"
date: 2011-04-16
forum: General Help
---

### Post by SWilliams on 2011-04-16
When I do:
> sudo apt-get install umbrello

I get:
> Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 umbrello : Depends: kdebase-runtime but it is not going to be installed
            Depends: libkde3support4 (>= 4:4.3.4) but it is not going to be installed
            Depends: libqt4-qt3support (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

Using Ubuntu 11.04

Thank you

---

### Post by spikoley on 2011-04-18
> This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

My guess is the packages aren't in the repository yet since 11.04 isn't out yet.

---

