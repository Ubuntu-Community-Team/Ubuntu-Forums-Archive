---
title: "Error when trying to update in 11.04 ubuntu"
date: 2011-05-28
forum: General Help
---

### Post by fullmetaljacket on 2011-05-28
Started today, when i click on update manager, it starts to search for updates then I get this error

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'


anyone know how to fix this

---

### Post by Rubi1200 on 2011-05-29
Hi and welcome to the forums :-)

Run these commands in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by fullmetaljacket on 2011-05-29
thank you very much, that worked... much appreciated

---

### Post by Rubi1200 on 2011-05-29
> **fullmetaljacket said:**
> thank you very much, that worked... much appreciated
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

