---
title: "GDebi Installer Problem"
date: 2010-06-29
forum: General Help
---

### Post by Hman242 on 2010-06-29
For the past week, I haven't been able to install anything using GDebi. Every time I do, it says that only one software managment tool may be open at once. It always says this, despite it being the only one open. What's wrong?

---

### Post by kalistona on 2010-06-29
do you thing your ubuntu is doing a big lie only for you ? if it is written 'only one tool...'it means that you have certainly or a bug (bad installed) or another tool open.

---

### Post by arrange on 2010-06-29
Could you post the output of this command from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?```
sudo lsof /var/lib/dpkg/*
```It should list the applications that are blocking your query.

---

### Post by dino99 on 2010-06-29
hidden sessions or some ghost around ?  :p

---

### Post by Hman242 on 2010-07-01
Damn, I forgot about this somehow. Sorry about that.
> **arrange said:**
> Could you post the output of this command from the [Terminal]("https://help.ubuntu.com/community/GnomeTerminal")?```
sudo lsof /var/lib/dpkg/*
```It should list the applications that are blocking your query.
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/hunter/.gvfs
      Output information may be incomplete.
```

---

### Post by arrange on 2010-07-01
When you try installing via *Synaptic* or *Software Center*, does it say the same?

---

### Post by Hman242 on 2010-07-04
Sorry for not posting again, I keep getting caught up in things.

So, I tried installing packages through the Software Center and Synaptic and they had problems too. Synaptic told me I needed to run this.
```
sudo dpkg --configure -a
```
I did and it fixed the problem.

---

