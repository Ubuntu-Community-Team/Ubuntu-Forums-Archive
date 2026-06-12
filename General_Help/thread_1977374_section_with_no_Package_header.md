---
title: "section with no Package: header"
date: 2012-05-10
forum: General Help
---

### Post by miros2 on 2012-05-10
Hello,
I recently upgraded to 12.04 that worked fine including to install updates until yesterday when I got the following message :
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-fr%5fFR, E:Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus.'
Could somebody help me to solve this problem (I'm not informatician!).
Thanks a lot

---

### Post by Rubi1200 on 2012-05-12
Hi and welcome to the forums :-)

open a terminal with Ctrl+Alt+T and copy/paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

click Enter after each one. The first command removes corrupted package lists, the second one refreshes them.

Let us know if this helps.

---

