---
title: "VLC  video interface"
date: 2009-08-27
forum: General Help
---

### Post by BlackSwordD2 on 2009-08-27
ok so im not sure when it happened, but somewhere down the line VLC had an integrated video and player. now they are in separate windows. is there anyway i can set VLC to be back into one window?

---

### Post by starcraft.man on 2009-08-27
> **BlackSwordD2 said:**
> ok so im not sure when it happened, but somewhere down the line VLC had an integrated video and player. now they are in separate windows. is there anyway i can set VLC to be back into one window?

This is a known bug with version of VLC in the repositories, only fix is to move up to the 1.00 release. Luckily, a ppa version exists, ya just add it to your sources list, down the key and then update to new version in 3 steps. Open any terminal and repeat the following (copy paste). In ubuntu, Applications > Accessories > terminal.

1. Add key.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D
```

2. Add repository.

```
sudo bash -c "echo 'deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main' >> /etc/apt/sources.list"

sudo bash -c "echo 'deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main' >> /etc/apt/sources.list"
```

3. Upgrade

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BlackSwordD2 on 2009-08-27
thank you! youre awesome and always seem to solve my problems

---

### Post by starcraft.man on 2009-08-27
> **BlackSwordD2 said:**
> thank you! youre awesome and always seem to solve my problems

Hehe, no worries, your welcome. I'm just the friendly canuck doing my part. :)

---

