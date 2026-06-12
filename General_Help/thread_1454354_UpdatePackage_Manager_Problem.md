---
title: "Update/Package Manager Problem"
date: 2010-04-14
forum: General Help
---

### Post by BRFC on 2010-04-14
Could anyone shed any light on the following and how I can put it right.
I got the following message from the Package Manager;

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Any help welcome, cheers Chris

---

### Post by darolu on 2010-04-14
> ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages
Open Synaptic and disable this repository. Then update your list.

That ppa pidgin repo is probably down, try enabling it after 24-48hours and try again.
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by BRFC on 2010-04-14
Thanks for the advice, repo removed and all sorted.

Cheers 

Chris

---

