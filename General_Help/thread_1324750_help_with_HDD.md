---
title: "help with HDD"
date: 2009-11-12
forum: General Help
---

### Post by davewave918 on 2009-11-12
novice ubuntu user here...so assume i know nothing about the os pls :)

have a 120gb hdd connected via sata raid controller. the card see's the drive, it has been initialized and created as a jbod. when i boot to ubuntu 9.10 from the gui i can go to system>administration>disk utility and the drive is listed there but:

it says "no media detected" - then there is a button to detect media, when i click it nothing happens.

next to the icon for this drive it says unknown size, no media detected, smart is not available, /dev/sdb

so i imagine there is some groovy command i dont know *yet* that may allow me to access this drive? i am thinking i have to fdisk and format it?

---

### Post by davewave918 on 2009-11-12
root@lx-ds:/home/ds# fdisk /dev/sdb

Unable to open /dev/sdb
root@lx-ds:/home/ds#

---

### Post by davewave918 on 2009-11-13
bumping....anyone? anyone? bueller? bueller?

---

### Post by davewave918 on 2009-11-16
well it turned out i was able to fix this one myself. just posting back here in case anyone has a similar problem.

ended up low level formatting the drive from my sata raid card, initialized the drive, then instead of using the jbod config i use a standard raid 1 config.

---

