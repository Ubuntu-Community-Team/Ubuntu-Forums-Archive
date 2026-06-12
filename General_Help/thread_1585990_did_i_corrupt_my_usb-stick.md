---
title: "did i corrupt my usb-stick?"
date: 2010-10-01
forum: General Help
---

### Post by Wakawakamush on 2010-10-01
hi,

i was writing a .img file to my usb stick with ImageWriter, but it didn't seem to do anything so i clicked the close gtk button and pulled the stick out of my pc. now my pc gives my an when i try to open the stick. is there any way to fix this. I can use win xp pro, win xp media center, win 7 starter, ubuntu 9.10 and ubuntu 10.04

---

### Post by SlugSlug on 2010-10-01
easeyst would be to re-format it -- will lose all data 

sudo apt-get install gparted 

then select partition editor from admin menu

---

### Post by Wakawakamush on 2010-10-01
thanks for the tip, but i cant find the name of my usb stick. it should be something like dev/... how do i discover that name. i don't want to format the wrong drive.

---

### Post by Wakawakamush on 2010-10-01
hehe, the name was in my screenshot. (Dev/sdb2)

---

### Post by SlugSlug on 2010-10-01
> **Wakawakamush said:**
> hehe, the name was in my screenshot. (Dev/sdb2)


aye /dev/sdb   -- you could just look at the sizes

---

### Post by Wakawakamush on 2010-10-01
Thanks for helping me! you are great!

---

