---
title: "Update manager"
date: 2010-02-13
forum: General Help
---

### Post by luisata on 2010-02-13
Hi, I was trying to run the update manager as usual, but I received this message
"'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"
Can anyone help? It looks as if the manager cannot operate and is completely stuck.:confused:
I'm fairly new to ubuntu and really don't have a clue about what to do. 
Thank you!!!

---

### Post by ubudog on 2010-02-13
Open a terminal (Applications>Accessories>Terminal) and type ```
sudo apt-get update
``` Enter your password (it won't show it) and press enter. Then try.  Also let me know if there are any error messages at the end.;)

---

### Post by paul_in_london on 2010-02-13
Running these commands should fix it:

```
sudo rm -vf /var/lib/apt/lists/*
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -vf /var/cache/apt/*.bin
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by ubudog on 2010-02-13
> **paul_in_london said:**
> running these commands should fix it:

```
sudo rm -vf /var/lib/apt/lists/*
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -vf /var/cache/apt/*.bin
sudo aptitude update
sudo aptitude upgrade

```

+1

---

