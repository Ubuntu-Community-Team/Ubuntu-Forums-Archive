---
title: "Software Center and Synaptic Package Manager help"
date: 2011-09-04
forum: General Help
---

### Post by Vepres on 2011-09-04
I just installed Linux Ubuntu this morning and I was trying to install new applications and I got an error under Software center that said the package loading failed. So I looked online to see if there was any help, and the website said to try Synaptic Package Manager. When I went on to Synaptic Package Manager, I got the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report. 

Any help that I could receive would be greatly appreciated.

---

### Post by oldos2er on 2011-09-05
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by Vepres on 2011-09-05
Thank you!

---

