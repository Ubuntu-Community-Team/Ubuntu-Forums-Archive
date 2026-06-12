---
title: "apt-get -f install"
date: 2012-09-20
forum: General Help
---

### Post by ckrugo on 2012-09-20
I was told by apt-get to run a 'apt-get -f install' to resolve some issues installing a new package. After running this command it tells me 486MB of stuff is going to be removed, if I agree. 

Can someone point me to an explanation of what this option does? It looks to be a clean up command of some sort.

---

### Post by jrog on 2012-09-20
> **ckrugo said:**
> I was told by apt-get to run a 'apt-get -f install' to resolve some issues installing a new package. After running this command it tells me 486MB of stuff is going to be removed, if I agree. 

Can someone point me to an explanation of what this option does? It looks to be a clean up command of some sort.
```
man apt-get
```

>        -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. If packages are specified, these have to completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(1) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

---

### Post by oldos2er on 2012-09-21
> **ckrugo said:**
> I was told by apt-get to run a 'apt-get -f install' to resolve some issues installing a new package. After running this command it tells me 486MB of stuff is going to be removed, if I agree. 

Can someone point me to an explanation of what this option does? It looks to be a clean up command of some sort.

Can you copy and paste all the terminal output here so we can see?

---

