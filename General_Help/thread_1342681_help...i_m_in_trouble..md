---
title: "help...i m in trouble."
date: 2009-12-01
forum: General Help
---

### Post by rahilm on 2009-12-01
I had a triple boot of ubuntu 9.10 9.04 and XP where Xp was in the first partition..
then i installed Windows 7 in place of Xp.
Which has replaced the MBR and even the partition table.
When i boot with the live CD.. the partition editor does not show any partition..
see attachment..for what it looks like.
but it other applications detect my partitions as you can see in the background..

---

### Post by Primefalcon on 2009-12-01
> **rahilm said:**
> I had a triple boot of ubuntu 9.10 9.04 and XP where Xp was in the first partition..
then i installed Windows 7 in place of Xp.
Which has replaced the MBR and even the partition table.
When i boot with the live CD.. the partition editor does not show any partition..
see attachment..for what it looks like.
but it other applications detect my partitions as you can see in the background..
windows probably wiped grub, you'll have to reinstall it

check this out
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by rahilm on 2009-12-01
9.10 has grub2

---

### Post by Primefalcon on 2009-12-01
> **rahilm said:**
> 9.10 has grub2
hmm yes I'm still using the old grub on 9.10 sorry, I like handling the config file myself... what can I say

try this
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by rahilm on 2009-12-01
i'll try it

---

### Post by wilee-nilee on 2009-12-01
Do you have more then one HD?

---

### Post by rahilm on 2009-12-01
> **wilee-nilee said:**
> Do you have more then one HD?
NO

I have successfully re-installed grub2..both ubuntu's are bootable..but still gparted shows nothing..
I'm worried since it will create problems when i will install Lucid hal a year later..or if i want to try another distro

---

### Post by rahilm on 2009-12-01
bump....

---

