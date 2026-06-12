---
title: "Error message/Packages"
date: 2011-06-05
forum: General Help
---

### Post by mavazz on 2011-06-05
Hi everyone!

I have an error message that I do not understand nor know how to resolve:
E: encountered a section with no Package:header
E: Problem with MergeList/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache>open() failed, please report.

I hope this is simple for some of you!!!  I do not have a clue what this means, I'm pathetic.

Thanks, folks!

Mavazz  :confused::confused:

---

### Post by Rubi1200 on 2011-06-05
Hi,

open a terminal and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by mavazz on 2011-06-05
> **Rubi1200 said:**
> Hi,

open a terminal and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
Rubi1200:

I had my son install your fix and so far, so good!!!  Thank you so much for your prompt help.  Life is much better now!

Mavazz

---

### Post by Rubi1200 on 2011-06-06
No problem, you are more than welcome :)

Please mark this Solved using the Thread Tools near the top of the page.

---

