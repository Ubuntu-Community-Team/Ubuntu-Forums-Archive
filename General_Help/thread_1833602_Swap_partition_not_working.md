---
title: "Swap partition not working"
date: 2011-08-26
forum: General Help
---

### Post by koleoptero on 2011-08-26
I run ubuntu 10.10 on a partition. Recently I installed swift linux on another to check it out and since then whenever I boot into ubuntu my swap space is 0. Any idea how to fix this? It has happened before when I installed other linux distributions as well so it's not an antix/swiftlinux thing.

---

### Post by fdrake on 2011-08-26
do you use a swap file or swap partition?

post results for:
```
swapon -s
free -k
```

---

### Post by coffeecat on 2011-08-26
Some Linux installers (not Ubuntu's) reformat a pre-existing swap partition which leads to a change of its UUID. (In fact the Ubuntu installer does reformat swap but it retains the old UUID.) If the UUID has changed the swap UUID in /etc/fstab will be wrong. From Ubuntu post the output of:

```
sudo blkid
cat /etc/fstab
```

---

### Post by koleoptero on 2011-08-26
Indeed the UUID had changed. I set it to the new one in /etc/fstab and now it works as it should. Many thanks for the help. :)

P.S.: It's a swap partition.

---

