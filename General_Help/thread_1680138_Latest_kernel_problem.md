---
title: "Latest kernel problem"
date: 2011-02-02
forum: General Help
---

### Post by aldee96 on 2011-02-02
I was do an update, and i see ther's a kernel package it's **.6.35-25 i download the updates, but  i was cancelled because i don't have much time for so i click cancel and continue it later. at first update it was about 215Mb but after the next day it's just 149Mb. i left it minimized and do the update, but after restart **[COLOR=Red]grub(with burg)[/COLOR]** the list of kernel wasn't changed it's still **.6.35-24 the older kernel. i tried to install the *.deb file in /var/cache/apt/archives but it's give me no effect, is there anyway to update the kernel manually or automatically to the latest

---

### Post by plucky on 2011-02-02
> **aldee96 said:**
> I was do an update, and i see ther's a kernel package it's **.6.35-25 i download the updates, but  i was cancelled because i don't have much time for so i click cancel and continue it later. at first update it was about 215Mb but after the next day it's just 149Mb. i left it minimized and do the update, but after restart **[COLOR=Red]grub(with burg)[/COLOR]** the list of kernel wasn't changed it's still **.6.35-24 the older kernel. i tried to install the *.deb file in /var/cache/apt/archives but it's give me no effect, is there anyway to update the kernel manually or automatically to the latest

Did you download the rest of updates?

Try from a terminal ```
sudo apt-get update
sudo apt-get upgrade
```

Good Luck

---

### Post by aldee96 on 2011-02-02
> **plucky said:**
> Did you download the rest of updates?

Try from a terminal ```
sudo apt-get update
sudo apt-get upgrade
```Good Luck


i've tried it before and it says that my computer is up to date, i think i need a specific kernel update to the latest known update today

---

### Post by plucky on 2011-02-02
See if it is in /boot directory with ```
ls /boot
``` which will show > vmlinuz-2.6.35-25-generic

If it is there,run ```
sudo update-grub
``` to add it to the grub list.

If it not there, run ```
sudo dpkg --configure -a
``` to see if it is unpackaged and not yet configured.

Good Luck

---

### Post by aldee96 on 2011-02-02
> **plucky said:**
> See if it is in /boot directory with ```
ls /boot
``` which will show 

If it is there,run ```
sudo update-grub
``` to add it to the grub list.

If it not there, run ```
sudo dpkg --configure -a
``` to see if it is unpackaged and not yet configured.

Good Luck


is it alright to do```
sudo update-grub
``` with a grub that covered by burg?

---

