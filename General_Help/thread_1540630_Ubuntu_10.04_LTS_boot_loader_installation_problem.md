---
title: "Ubuntu 10.04 LTS boot loader installation problem"
date: 2010-07-28
forum: General Help
---

### Post by weissnich on 2010-07-28
I want to install grub on the ubuntu root partition because I have another boot loader (boot-us).
But when I reach : device for boot loader installation and set the device to the root partition (/dev/sda3) the OK button is not highlighted, I can use the windows partitions but not ubuntu root partition, what goes wrong?

---

### Post by weissnich on 2010-07-28
This is weird, I can't get grub installed on the root partition, is this a problem with grub 2 ?

---

### Post by dino99 on 2010-07-28
with synaptic: remove/purge grub-pc then reinstall it on /dev/sda when asked (only grub-pc and grub-common have to be installed, remove menu.lst if it exist)

---

### Post by varunendra on 2010-07-28
> **weissnich said:**
> This is weird, I can't get grub installed on the root partition, is this a problem with grub 2 ?

[This]("http://ubuntuforums.org/showthread.php?t=1339771") thread seems to contain the answer & solution for you. (ref. to post #5, however, the whole discussion is really informative and interesting)

---

