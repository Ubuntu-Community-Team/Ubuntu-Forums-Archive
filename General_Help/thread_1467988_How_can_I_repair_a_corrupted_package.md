---
title: "How can I repair a corrupted package?"
date: 2010-05-01
forum: General Help
---

### Post by johnnymenmonic on 2010-05-01
I have a problem with a corrupted package. The download fails even if I switch to different servers. I think that the package is corrupted but I have no idea how to repair it.

---

### Post by dino99 on 2010-05-01
try : 
sudo dpkg --configure -a

if you know the exact package name (watch: system admin log viewer or .xsession-errors in the /home dir), you can goto synaptic and remove/purge it then reinstall it

then

sudo apt-get install -f

are you using third party repo or custom package ?

---

