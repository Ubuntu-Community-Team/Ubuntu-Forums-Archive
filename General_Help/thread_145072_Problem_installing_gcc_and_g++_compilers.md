---
title: "Problem installing gcc and g++ compilers"
date: 2006-03-15
forum: General Help
---

### Post by Snargledorf on 2006-03-15
When installing the compilers via apt-get or synaptic i get this error

> snargledorf@snargledorf:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
E: Broken packages


I try to apt-get the packages it say but it just comes up with more errors.

ive tries the wiki and i still cant find nething so pls post thank you

---

