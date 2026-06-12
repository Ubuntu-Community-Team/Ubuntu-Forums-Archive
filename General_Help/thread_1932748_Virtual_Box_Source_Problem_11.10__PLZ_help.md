---
title: "Virtual Box Source Problem 11.10  PLZ help"
date: 2012-02-28
forum: General Help
---

### Post by elladjalov on 2012-02-28
Hello, I am using Ubuntu 11.10, everything was running fine until i tried to instal  virtual box. Now i cant open anything synaptic nor ubuntu update manager. Anyone please help here is the code i get when i try to open synaptic

E: Type 'wget' is not known on line 1 in source list /etc/apt/sources.list.d/virtualbox.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by wildmanne39 on 2012-02-28
Hi, did you add it to your source list? that is what it looks like if so remove it and run:
```
sudo apt-get update
```
'wget' does not belong in your source list.
Thanks

---

