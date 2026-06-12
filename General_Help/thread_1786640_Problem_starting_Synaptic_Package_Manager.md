---
title: "Problem starting Synaptic Package Manager"
date: 2011-06-19
forum: General Help
---

### Post by dmugambi on 2011-06-19
I am getting the following error whenever I start up Synaptic Package Manager. The dialogue box reads:

An error occurred, the following details are provided.

[INDENT]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/INDENT]

and then I click 'close' (the only option available) and Synaptic closes.

---

### Post by wildmanne39 on 2011-06-19
> **dmugambi said:**
> I am getting the following error whenever I start up Synaptic Package Manager. The dialogue box reads:

An error occurred, the following details are provided.

[INDENT]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/INDENT]

and then I click 'close' (the only option available) and Synaptic closes.
Hi,this commands should get you going
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

