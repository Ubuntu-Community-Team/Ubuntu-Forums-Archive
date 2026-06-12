---
title: "Cannot install packages, always locked"
date: 2011-09-28
forum: General Help
---

### Post by kabeza on 2011-09-28
Hi
I'm having some kind of trouble because everytime I want to install a package, I get 

[B]E: Could not block /var/lib/apt/lists/lock - open (11: Resource not available temporarily)
[/B]

One solution is to go /var/lib/apt/lists and do sudo rm lock, but I have to do even if I restart the PC/OS, so I'm assuming there's something that runs at boot that locks that file/folder and blocks APT work

How can I log which app/etc locks/blocks that thing at startup and kill it?

I still have the same apps running at startup but I begun having this behaviour since some days ago

Thanks

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-28
Are you sure Synaptic isn't running, or that an update isn't being installed, etc?

---

### Post by dino99 on 2011-09-28
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

---

### Post by kabeza on 2011-09-28
> **OpEn_SoUrCe_RoCkS said:**
> Are you sure Synaptic isn't running, or that an update isn't being installed, etc?


synaptic nor software centre are running

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-28
Try:
```
sudo lsof /var/lib/apt/lists/lock
```

This will tell you what processes are using the lock file.

Then, you can kill them with:
```
sudo kill -9 [processnumber]
```

---

### Post by kabeza on 2011-09-29
> **dino99 said:**
> sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean


This solved the problem. Seems I had some installation garbage

---

