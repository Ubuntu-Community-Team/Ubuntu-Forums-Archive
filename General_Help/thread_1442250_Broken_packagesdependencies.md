---
title: "Broken packages/dependencies?"
date: 2010-03-29
forum: General Help
---

### Post by luke2ekul on 2010-03-29
I tried installing virtual box 3.1 but messed up, and now i have a broken package which wont let me do anything. when ever i try to "apt-get install -f" it doesn't work. it won't let me remove the package either. all it says that it needs to be reinstalled but can't find an archive for it

```
luke@rune:~$ su
Password: 
root@rune:/home/luke# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-3.1 needs to be reinstalled, but I can't find an archive for it.
root@rune:/home/luke# apt-get remove virtualbox-3.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-3.1 needs to be reinstalled, but I can't find an archive for it.
root@rune:/home/luke# 

```
EDIT: i solved this with "dpkg --remove --force-remove-reinstreq"

---

