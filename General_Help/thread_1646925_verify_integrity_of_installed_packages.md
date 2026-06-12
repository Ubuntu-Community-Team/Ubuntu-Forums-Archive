---
title: "verify integrity of installed packages"
date: 2010-12-16
forum: General Help
---

### Post by fa2k on 2010-12-16
Hi, I am experiencing some strange behaviour with  sound, and I have been messing around with installing some  ALSA drivers. I suspect that I might have corrupted some part of the installed Ubuntu packages. 

Is there a way to check all the packages on the system for integrity using apt-get or similar?

Marius

---

### Post by amauk on 2010-12-16
Install debsums```
sudo apt-get install debsums
```

Debsums will verify the files on your system against the files in the package repositories (and tell you if they differ)

Most packages include the neccessary info to verify them against the repositories, but some don't, so first up, run```
sudo debsums_init
```This will generate file hashes for any packages that lack them (note, this involves downloading the package from the repositories)

Then you can run the verification```
sudo debsums -c
```

---

### Post by fa2k on 2010-12-17
Thanks, that command is absolutely brilliant! (Found some things, but i don't think that was the problem)

---

