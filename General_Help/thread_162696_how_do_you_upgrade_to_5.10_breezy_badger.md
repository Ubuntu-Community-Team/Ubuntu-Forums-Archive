---
title: "how do you upgrade to 5.10 breezy badger?"
date: 2006-04-19
forum: General Help
---

### Post by Muag on 2006-04-19
Long story short...my 5.10 cd was corrupt so someone gave me the other version 5.04 to install, so now i need to know how to upgrade it to 5.10...thanks.

---

### Post by oscar on 2006-04-19
See this guide on the wiki:
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)
I think the easiest way is to use the "Apt-Get" method.

---

### Post by uantuzri on 2006-04-19
very easy:

```
sudo apt-get update
sudo apt-get upgrade
```

You can also make this with grafically: System>Administration>Update manager (or something like this)

---

### Post by uantuzri on 2006-04-19
ooups, we wrote at the same time. It'll be better if you follow the wiki instructions!

---

### Post by Muag on 2006-04-19
alright thanks!

---

### Post by oscar on 2006-04-19
Muag, you have 5.04 installed so it is not just those commands that you have to use. To use those commands you first have to update your sources.list to the breezy repositories, as in the wiki entry I linked to. Without first doing that all those commands will do it get you the latest updates for *hoary* not breezy.

From the wiki entry:
> Apt-Get

   1. Open up a terminal
   2. sudo gedit /etc/apt/sources.list (for ubuntu/edubuntu) kdesu kwrite /etc/apt/sources.list (for Kubuntu)
   3. Replace with the following:

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

   1. sudo apt-get update
   2. sudo apt-get dist-upgrade


---

