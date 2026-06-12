---
title: "Installing Starcraft 2 with wine (libssl-dev problem0"
date: 2010-05-09
forum: General Help
---

### Post by BoudewijnD on 2010-05-09
I want to install Starcraft 2 using wine like on the following WineHQ website: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376")

But when I do the following command: ```
sudo apt-get build-dep wine
```

Then I get the following error message ```
boudewijn@boudewijn-desktop:~/wine-git$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-16ubuntu3.1) but 0.9.8k-7ubuntu8 is to be installed
E: Build-dependencies for wine could not be satisfied.
```

Can some body please help me??

Thanx 
\BoudewijnD

---

### Post by Jackp90 on 2010-08-14
Have you tried installing libssl0.9.8?

```
sudo apt-get install libssl0.9.8
```

---

