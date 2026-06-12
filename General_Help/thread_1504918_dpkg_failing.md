---
title: "dpkg failing"
date: 2010-06-08
forum: General Help
---

### Post by wolfmanz51 on 2010-06-08
Solved!
on 10.4 when i try to use update manger or synaptic to istall stuff i get this error
dpkg: unrecoverable fatal error, aborting: syntax error: unknown group 'cdemu' in stateoverride file E: Sub-process /user/bin/dpkg returned error code 2 a package failed to install. trying to recover

What i did is i created the group cdemu under users and groups thanks for trying guys but [this]("http://ubuntuforums.org/showthread.php?t=1498899&highlight=unknown+group+stateoverride+file") is what helped

---

### Post by wolfmanz51 on 2010-06-08
anybody?

---

### Post by wolfmanz51 on 2010-06-09
please?:/

---

### Post by dino99 on 2010-06-09
check your synaptic repo, be sure to use the main server and only genuine lucid repo (no mixed distro, no third party, no ppa)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by SlidingHorn on 2010-06-09
Hey, thanks for your patience, and sorry it's taking a while to get responses.  Have you checked out this post?  Someone had a similar issue [here]("http://ubuntuforums.org/showpost.php?p=8024918&postcount=7")

---

### Post by wolfmanz51 on 2010-06-10
scratch that its still not working and 
#sudo dpkg --configure -a does not work

---

### Post by dino99 on 2010-06-10
from where come this "cdemu" ?

install locate, and into a terminal: locate cdemu

then remove everything about "cdemu"

you can clean your system too by installing and using gconf-cleaner (yes to all) and bleachbit

---

