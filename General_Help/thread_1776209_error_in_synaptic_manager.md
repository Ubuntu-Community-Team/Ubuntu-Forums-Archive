---
title: "error in synaptic manager"
date: 2011-06-05
forum: General Help
---

### Post by grey_ghost on 2011-06-05
hi,
       i am getting problem with my synaptic manager,when ever i tried to open it,it show me error message
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by wildmanne39 on 2011-06-05
> **grey_ghost said:**
> hi,
       i am getting problem with my synaptic manager,when ever i tried to open it,it show me error message
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
Hi, try this command in a terminal, if it does not fix it post your version of ubuntu that you are using.
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by grey_ghost on 2011-06-06
hi, 
i am using ubutnu 11.04 version. now i am able to open the synaptic manager but its shoeing the message that "you have 6 broken package on your system."

thanks in advance

---

### Post by wildmanne39 on 2011-06-06
> **grey_ghost said:**
> hi, 
i am using ubutnu 11.04 version. now i am able to open the synaptic manager but its shoeing the message that "you have 6 broken package on your system."

thanks in advanceHi, try this in a terminal.
```
sudo apt-get install -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

