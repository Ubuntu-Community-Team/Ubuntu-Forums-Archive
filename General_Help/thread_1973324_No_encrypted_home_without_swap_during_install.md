---
title: "No encrypted home without swap during install"
date: 2012-05-04
forum: General Help
---

### Post by ppparadox on 2012-05-04
[COLOR="Red"]*** _[SIZE="3"]Angry post warning[/SIZE]_ ***[/COLOR]
Ok Ubuntu, this is a deal breaker.
You can ask me to overlook all the crashes and consequent apport reports that keep popping up all the time, but you can't f**k with my security.
No more ubuntu for me after this one.
Due to this confirmed bug --> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/991139](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/991139)
I was unable to natively encrypt my home upon installation.
Now for the question:
**is there a way to setup the encrypted home *after* the installation process?**

---

### Post by PhantomTurtle on 2012-05-04
Well, not all bugs can be worked out. It takes time, so give it some time. Anyway here is a guide on how to encrypt your /home folder AFTER installation - [http://ubuntuforums.org/showthread.php?t=1449168]("http://ubuntuforums.org/showthread.php?t=1449168"). I haven't done it so I probably won't be able to help you much more.

---

### Post by ratcheer on 2012-05-04
> **ppparadox said:**
> [COLOR=Red][/COLOR]
Now for the question:
**is there a way to setup the encrypted home *after* the installation process?**

Wouldn't it be simpler to just give it a swap partition?

Tim

---

### Post by ppparadox on 2012-05-04
> **PhantomTurtle said:**
> Well, not all bugs can be worked out. It takes time, so give it some time. 
While i agree with you i must say that you simply cannot let slip through a bug like this. *It's the installer goddammit.*
No excuse for that.
> **PhantomTurtle said:**
> 
Anyway here is a guide on how to encrypt your /home folder AFTER installation
Thanks, will definitely try that after *yet another backup* (after the one for the botched install).

> **ratcheer said:**
> Wouldn't it be simpler to just give it a swap partition?
I'm gonna keep the rude answer to myself...
Polite answer: had i had any clue of what the problem was (at install time) i might have tried with a small swap partition i'd have deleted later.

---

### Post by vagabond_gr on 2012-06-02
I had the same issue, so I thought to post a workaround, which is simply to create a swap partition during installation, then delete it afterwards and merge back the unused space into the main partition. It's much easier than starting without encryption and adding it later.

1. During installation, select a 1GB swap partition. If you want to reclaim the space afterwards the partition needs to be adjacent to the one you want to merge it with. Also check the option to encrypt the home directory.

2. After the installation is over and you have booted ubuntu, do the following to disable the swap:

```
sudo swapoff -a
sudo cryptsetup remove /dev/mapper/cryptswap1
sudo vim /etc/crypttab
*remove the /dev/sda5 line
sudo vim /etc/fstab
*remove the /dev/mapper/cryptswap1 line
```

3. Now the swap partition is not used. Boot back into the ubuntu install cd, select "try ubuntu", open GParted, delete the swap partition and resize  your main partition to include the swap's space.

---

### Post by Paddy Landau on 2012-06-02
Does this help?

[How to encrypt after creating a user]("http://ubuntuforums.org/showthread.php?t=1987630").

---

