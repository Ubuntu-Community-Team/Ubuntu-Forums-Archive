---
title: "update manager"
date: 2011-06-08
forum: General Help
---

### Post by michael_j on 2011-06-08
I get this message when trying to use the Update Manager in 11.04

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

and immediate shutdown of update manager

---

### Post by linuxinstalledfromhdd on 2011-06-08
You can try this in your terminal:
```

sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update
```

---

### Post by seawolf167 on 2011-06-08
> **linuxinstalledfromhdd said:**
> You can try this in your terminal:
```

sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get ***update***
sudo apt-get ***upgrade***
```

Aye - I just answered another thread with the same error message and this worked for him (the modded quote above)

---

