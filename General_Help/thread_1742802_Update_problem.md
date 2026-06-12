---
title: "Update problem"
date: 2011-04-29
forum: General Help
---

### Post by Zlatan on 2011-04-29
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

Get this kind of error while trying to update Natty. Please help, thank you

---

### Post by imigueldiaz on 2011-04-29
> **Zlatan said:**
> ```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

Get this kind of error while trying to update Natty. Please help, thank you

I would backup /var/lib/apt/lists/ contents, and later

```

sudo rm -rf /var/lib/apt/lists/*
sudo aptitude update

```

because MergeList seems to be corrupted.

Best

---

### Post by dino99 on 2011-04-29
Stop upgrading, the servers are too busy right now, wait for next week to do it

---

### Post by leonkou on 2011-04-29
There is a problem with 11.04 installation and update. Tried to do clean install on two different computers and both failed. I 'll stick on 10.10 for the time being until everything is fixed.

---

### Post by Zlatan on 2011-04-29
> **imigueldiaz said:**
> I would backup /var/lib/apt/lists/ contents, and later

```

sudo rm -rf /var/lib/apt/lists/*
sudo aptitude update

```

because MergeList seems to be corrupted.

Best

sorry mate, still same problem here

---

### Post by Zlatan on 2011-05-03
OK, that's it, wireless broken, updates do not work, see you in latest LTS;)

---

