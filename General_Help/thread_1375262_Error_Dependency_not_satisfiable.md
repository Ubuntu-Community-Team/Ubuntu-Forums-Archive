---
title: "Error: Dependency not satisfiable"
date: 2010-01-07
forum: General Help
---

### Post by bluestar14 on 2010-01-07
i am trying to install gloobus, but when i open deb package it says Error: Dependency is not satifiable  :(

---

### Post by zvacet on 2010-01-08
```
sudo apt-get -f install
```

or add one of [these]("https://launchpad.net/ubuntu/+ppas?name_filter=gloobus") repos t oyour source list.After that 

```
sudo apt-get update
```

---

