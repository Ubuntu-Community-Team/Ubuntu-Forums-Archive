---
title: "Why was gdebi removed from the default install?"
date: 2012-07-01
forum: General Help
---

### Post by Starks on 2012-07-01
I know I can install it, but is there no way to safely install a deb from the command line right out of the box?

dpkg is far to dangerous to use in most circumstances.

---

### Post by elliotn on 2012-07-01
sudo apt-get install gdebi

---

### Post by Starks on 2012-07-01
Install from a deb, I mean.

---

### Post by elliotn on 2012-07-01
> **Starks said:**
> I know I can install it, but is there no way to safely install a deb from the command line right out of the box?

dpkg is far to dangerous to use in most circumstances.

lol on second thought gdebi is there on the repository I believe, it is one of the first package I installed after a fresh 12.04 installation

---

### Post by elliotn on 2012-07-01
> **Starks said:**
> Install from a deb, I mean.

I haven't seen any other way of installing a deb without the dpkg method....

---

### Post by Starks on 2012-07-01
Can dpkg pull in dependencies?

---

### Post by elliotn on 2012-07-01
> **Starks said:**
> Can dpkg pull in dependencies?

extract the deb file and look somewhere in there, I forgot which folder but there is a text file that has the dependencies for each package, look in there

---

### Post by Starks on 2012-07-01
Thanks.

---

### Post by Cheesemill on 2012-07-01
dpkg itself won't install any dependancies but running apt get afterwards will:
```
dpkg -i package.deb
apt-get -f install
```

---

