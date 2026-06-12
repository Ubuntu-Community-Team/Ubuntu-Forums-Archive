---
title: "Upgrade Empathy on 9.04 Install Help"
date: 2009-12-15
forum: General Help
---

### Post by CrusaderAD on 2009-12-15
How do you install the latest empathy on 9.04? I did the instructions here:

[http://live.gnome.org/Empathy/Install]("http://live.gnome.org/Empathy/Install")

But when I run:

```
make && make install
```

I get an error:
make: *** No targets specified and no makefile found.  Stop.

Any help please?

---

### Post by Bucky Ball on 2009-12-15
In a terminal you could try:

```
sudo apt-get update
```Then:

```
sudo apt-get upgrade
```and that will upgrade any apps that are upgradeable in the repos.

---

### Post by CrusaderAD on 2009-12-16
I acutally added some repos to my software packages and ran the upgrade... the upgraded to the newest version which makes it possible to use audium themes :) I'll post the software sources here later today.

---

### Post by CrusaderAD on 2009-12-17
Here's the 3rd part source for empathy:
[http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu)

---

### Post by Bucky Ball on 2009-12-18
Please mark as solved so others might learn from your fix. ;)

---

