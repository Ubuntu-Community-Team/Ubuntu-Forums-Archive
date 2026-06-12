---
title: "unreadable drives"
date: 2011-09-30
forum: General Help
---

### Post by netopalis45 on 2011-09-30
I have tried to use a microSD card to boot Arch and now I need that card to be formatted but when I plug it into either of my computers it doesn't show up. I have tried using sudo fdisk -l and the built in disk utility and all they show is that it is a 32mb drive (the card is 8gb) and I am unable to format it. How can I recover this card so I can use it again?

---

### Post by dcstar on 2011-10-01
> **netopalis45 said:**
> I have tried to use a microSD card to boot Arch and now I need that card to be formatted but when I plug it into either of my computers it doesn't show up. I have tried using sudo fdisk -l and the built in disk utility and all they show is that it is a 32mb drive (the card is 8gb) and I am unable to format it. How can I recover this card so I can use it again?

Use **gparted** to write a new partition table to it.

---

### Post by netopalis45 on 2011-10-01
> **dcstar said:**
> Use **gparted** to write a new partition table to it.

Gparted doesn't even recognise that I have the disk plugged in

---

