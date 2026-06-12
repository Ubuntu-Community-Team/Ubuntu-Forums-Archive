---
title: "Synaptic Package Manager Bombs Out"
date: 2011-06-11
forum: General Help
---

### Post by OriTheEep on 2011-06-11
with this message...

[INDENT]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
[/INDENT]So I am reporting it here, not being certain of anywhere else to do so, and hoping that somebody can give instructions on how to get it going again.

Gnome is 2.32.0
Ubuntu is 10.10, variously upgraded since (?)8.04.

Cheers, everyone!

---

### Post by Rubi1200 on 2011-06-11
Hi,
run these commands in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by OriTheEep on 2011-06-11
> **Rubi1200 said:**
> Hi,
run these commands in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```


Thanks, Rubi, that's done the trick. :)

Any idea how it got into that state; I'm fairly certain it was nothing I did? :-k

---

### Post by Rubi1200 on 2011-06-12
Excellent! Glad this worked for you and thanks for marking this thread Solved :-)

---

