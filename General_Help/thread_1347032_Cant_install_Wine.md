---
title: "Cant install Wine"
date: 2009-12-05
forum: General Help
---

### Post by Saddl3r on 2009-12-05
Hi. When i try to install Wine, i get this:

jacob@jacob-desktop:~$ sudo apt-get install wine
[sudo] password for jacob:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

So does someone know what i should do? I installed Ubuntu an hour ago on a new partition.

---

### Post by zvacet on 2009-12-05
Applications>accessories>terminal and type

```
sudo apt-get -f install
```

---

### Post by Saddl3r on 2009-12-05
> **zvacet said:**
> Applications>accessories>terminal and type

```
sudo apt-get -f install
```

Nothing happend, it just said "0 to uppgrade, 0 to reinstall, 0 to remove and 0 to not uppgrade." (Freely translated from Swedish :P)

---

### Post by zvacet on 2009-12-05
System>admin>software sources>check all under Ubuntu software(except source) and first two under updates tab.Reload and then try to install wine from synaptic (or terminal).

---

