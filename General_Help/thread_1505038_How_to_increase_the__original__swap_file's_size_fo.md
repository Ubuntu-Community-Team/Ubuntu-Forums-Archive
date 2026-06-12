---
title: "How to increase the _original_ swap file's size for hibernate to work? (wubi install)"
date: 2010-06-08
forum: General Help
---

### Post by Asagrim on 2010-06-08
My problem is the following:

Wubi doesn't let me set the swap file size, so on installation it only creates a swap file of a few hundred megabytes. Because of this, i cannot hibernate my netbook (eeePC 1005HA), which has 2 GB of RAM.

Creating a 2 GB swap file alongside of the original one using the tutorial [here]("https://help.ubuntu.com/community/SwapFaq") did work, but hibernate doesn't seem to work with it. For this reason i thought increasing the original swap's size instead of creating more would be a way to solve my problem.

Any idea on how to do that?

---

### Post by jmszr on 2010-06-08
Asagrim,

> Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

From: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Seems like the only solution is to set up a dual-boot (or Ubuntu only) installation.

---

### Post by bcbc on 2010-06-10
According to the creator of wubi the problem with hibernation in wubi is more to do with the fact that hibernation under ubuntu does not work with a swap file, than a wubi problem itself. In the case of wubi, the swap is always a file. 

He went on to say that you could hibernate with wubi provided you set up a physical swap partition, but since the whole point of wubi is to be able to try ubuntu without having to partition your drive this doesn't make a whole lot of sense.

---

