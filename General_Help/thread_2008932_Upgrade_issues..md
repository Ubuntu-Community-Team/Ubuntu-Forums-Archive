---
title: "Upgrade issues."
date: 2012-06-23
forum: General Help
---

### Post by crcrangers3 on 2012-06-23
I am having an issue with downloading Distribution Upgrades for my Ubuntu Desktop. I go to do a partial download and it just freezes after a few seconds of downloading the updates. I am new to ubuntu and linux in general so I do not know where to look at first to fix this issue. Can someone help me please and thank you?


it is frozen on reading cache.

---

### Post by Redblade20XX on 2012-06-23
Since the gui is giving you some problems, lets try the terminal method (it will give us more details if anything happens!)

So first you will want to update your cache:

```
sudo apt-get update
```

Then you will want to upgrade all packages to there current versions.

```
sudo apt-get upgrade
```

Afterwards you'll want to begin the upgrade procedure. This will attempt to upgrade Ubuntu to 12.04. Make sure to make backups of any important files even when your doing a gui upgrade.

```
sudo apt-get dist-upgrade 
```

Post what happens after this point.

-Red

---

### Post by wildmanne39 on 2012-06-23
Hi, when it comes to a partial upgrade you should  almost never do one. 
[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)
Thanks

---

### Post by crcrangers3 on 2012-06-23
It says E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
           E: Unable to lock directory /var/lib/apt/lists/
          E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
          E: Unable to lock the administration directory (var/Lib/dpkg/), is another process using it?

---

### Post by wildmanne39 on 2012-06-23
Hi, make sure you do not have the terminal and software center open at the same time then try:
```

sudo rm /var/lib/apt/lists/lock
sudo apt-get clean
sudo apt-get update

```
Thanks

---

