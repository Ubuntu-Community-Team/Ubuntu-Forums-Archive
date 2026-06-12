---
title: "Update problems in 9.04"
date: 2010-02-24
forum: General Help
---

### Post by tiatlon on 2010-02-24
I have update problems in Ubuntu 9.04, when I click install updates, I have this error:

[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
[/B]
Also when I restart and launch Update Managers it for some strange reasons asks for disk of Xubuntu 8.04 (I don't remember installing Xubuntu)

What can I do about it?

---

### Post by 1/0 on 2010-02-24
Have you tried:

```
sudo dpkg -a --configure && sudo apt-get -f install
```

---

### Post by plucky on 2010-02-24
> **tiatlon said:**
> I have update problems in Ubuntu 9.04, when I click install updates, I have this error:

[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
[/B]


That means you have two package managers open.i.e Synaptic or aptitude or apt-get or update manager.You can only use one at a time.

> Also when I restart and launch Update Managers it for some strange reasons asks for disk of Xubuntu 8.04 (I don't remember installing Xubuntu)

What can I do about it?

**System > Administration > Software Sources** and un-tick the reference to the Xubuntu 8.04 CD.

Good Luck

---

### Post by tiatlon on 2010-02-25
> **plucky said:**
> That means you have two package managers open.i.e Synaptic or aptitude or apt-get or update manager.You can only use one at a time.



**System > Administration > Software Sources** and un-tick the reference to the Xubuntu 8.04 CD.

Good Luck

Thank you plucky, strangely Xubuntu 8.04 CD was selected, I don't remember selecting it, but may be I did it accidentally. I still needed to restart, because there were not any visible windows with update manager. May be the error with missing Xubuntu disk caused the software to leave some locks.

By the way, how to mark this thread solved?

---

### Post by MelDJ on 2010-02-25
thread tools-mark thread as solved

---

