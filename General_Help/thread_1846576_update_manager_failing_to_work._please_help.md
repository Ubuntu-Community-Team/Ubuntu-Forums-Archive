---
title: "update manager failing to work. please help"
date: 2011-09-19
forum: General Help
---

### Post by oteycri000 on 2011-09-19
Hello. I am new to the forums although i am not new to Ubuntu, since i´ve been using it since the 8.04 version came out. I downloaded ubuntu 11.04 a few months ago to my computer, replacing windows with ubuntu and everything worked out fine for awhile. But now i get a message from my update manager that´s like this:

" an unresolvable error occurred while initializing the package information. Please report this bug "against the update manager" package and include the following: 'E:Problem with Mergelist/var/lib/app/lists/us.archive.ubuntu.com_ubuntu_lists_natty_main_binary_i386_Packages,E:the package list or status file could not be parsed or open."

And my ubuntu software center isnt working also, i think it may be related to the update manager problem. Please help and i appreciate any help i can get or advice.

---

### Post by cipherboy_loc on 2011-09-19
Open up a terminal (Applications -> Accessories -> Terminal) and run the following:

```

sudo apt-get update && sudo apt-get upgrade

```This should fix the problem and run some updates, but you will want to check again from the update manager (for kernel updates). If you don't want to run the upgrade, type n at the prompt (Are you sure you want to continue? [Y/n])



Cipherboy

---

### Post by plucky on 2011-09-19
> **cipherboy_loc said:**
> Open up a terminal (Applications -> Accessories -> Terminal) and run the following:

```

sudo apt-get update && sudo apt-get upgrade

```This should fix the problem and run some updates, but you will want to check again from the update manager (for kernel updates). If you don't want to run the upgrade, type n at the prompt (Are you sure you want to continue? [Y/n])



Cipherboy

And  if that doesn't work, also from a terminal ```
sudo rm /var/lib/app/lists/* -vf
sudo apt-get update
```

Good Luck

---

### Post by oteycri000 on 2011-09-19
Thanks. i tried both of the ideas and the failed unfortunately. I´ll try to downgrade to a version i am more familiar with, like 10.04 lts. Thank you so much for your help though

---

### Post by Rubi1200 on 2011-09-19
Before you consider that, post the output of the following command:

```
cat /etc/apt/sources.list
```

---

