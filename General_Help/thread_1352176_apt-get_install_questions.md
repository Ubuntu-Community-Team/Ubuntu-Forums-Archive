---
title: "apt-get install questions"
date: 2009-12-11
forum: General Help
---

### Post by prem1er on 2009-12-11
1. I was trying to install a .deb package last night that had some dependency problems. When I tried to install it again I was suggested to run 

```
apt-get -f install
```

I have looked in the man pages and there is no mention of the -f parameter. What does it do?

2. When I ran 

```
apt-get -f install
```

it also compiled a list of packages that 'were installed, but not being used' and suggested I run,

```
apt-get autoremove
```

but some of the packages in that list I was definitely still using. Why was this suggested?

---

### Post by Bachstelze on 2009-12-11
> **prem1er said:**
> 1. I was trying to install a .deb package last night that had some dependency problems. When I tried to install it again I was suggested to run 

```
apt-get -f install
```

I have looked in the man pages and there is no mention of the -f parameter. What does it do?

Seems you haven't looked well enough. ;)

```
       -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place. This option, when used with
           install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is sometimes necessary when running APT for the
           first time; APT itself does not allow broken package dependencies to exist on a system. It is possible
           that a system´s dependency structure can be so corrupt as to require manual intervention (which usually
           means using dselect(8) or dpkg --remove to eliminate some of the offending packages). Use of this option
           together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

```

> **prem1er said:**
> 2. When I ran 

```
apt-get -f install
```

it also compiled a list of packages that 'were installed, but not being used' and suggested I run,

```
apt-get autoremove
```

but some of the packages in that list I was definitely still using. Why was this suggested?

Run

```
sudo apt-get install package
```

on every listed package that you need. This will tell Apt those packages were really installed by you (as opposed to being pulled as dependencies for another package), and it won't mark them as 'not being used' anymore.

This happens when you have package B installed as a dependency for package A, and package A is either uninstalled later, or doesn't need package B anymore. Apt will tell you that package B is not being used, and will suggest I uninstall it.

---

### Post by prem1er on 2009-12-11
Thank you for the explanation. I was an idiot and looking at the man pages for install instead of apt-get, that is why I couldn't find it. Thanks again!

---

