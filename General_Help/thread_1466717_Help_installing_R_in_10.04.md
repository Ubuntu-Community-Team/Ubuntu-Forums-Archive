---
title: "Help installing R in 10.04"
date: 2010-04-30
forum: General Help
---

### Post by StuartN on 2010-04-30
I am trying to install R in Ubuntu 10.04, but having trouble with dependencies. The package I am trying to install is the meta package r-base - I believe this is what I have used in all previous versions of Ubuntu, without any dependency issues.

I am stuck with tcl8.5 and tk8.5 that will neither install nor purge:

```
dpkg: error processing tcl8.5 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tk8.5:
 tk8.5 depends on tcl8.5 (>= 8.5.0); however:
  Package tcl8.5 is not configured yet.
dpkg: error processing tk8.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 tcl8.5
 tk8.5

```

---

### Post by StuartN on 2010-04-30
> **StuartN said:**
> I am stuck with tcl8.5 and tk8.5 that will neither install nor purge

I think this was simply corrupted during download - sudo rm /var/lib/dpkg/info/tcl8.5* followed by sudo apt-get purge tcl8.5, sudo apt-get install tcl8.5 sorted it out - r-base installed fine.

---

