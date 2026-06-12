---
title: "Ubuntu 10.04 booting with tty1 (without GUI)"
date: 2012-07-02
forum: General Help
---

### Post by richardpn on 2012-07-02
Hi all,

I have a dual boot on my PC, window XP and Ubuntu 10.04. Previously Ubuntu has been working fine. A few months never use Ubuntu and today can only boot to tty1 terminal. 

I can log in at tty1 terminal. when i type startx, show some server error. Also tried sudo apt-get upgrade || sudo apt-get update, no help. And on terminal, also mention something like "read only files system". Please help me with this.

PN

---

### Post by msammels on 2012-07-03
Hi richardpn,

Have you tried using the following modifier:

```
CTRL+ALT+F7
```

This is the default tty for the X server. Perhaps this will work. Also, can you post the exact output of:

```
sudo apt-get update
```

please?

---

