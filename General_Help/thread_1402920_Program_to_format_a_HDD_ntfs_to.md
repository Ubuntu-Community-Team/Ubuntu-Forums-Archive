---
title: "Program to format a HDD ntfs to"
date: 2010-02-09
forum: General Help
---

### Post by green69 on 2010-02-09
Hi Guys!

I just bought an external HDD (WD) which came with ntfs format. Which program can I use to reformat it to ext4? How can I do it?

Thank you in advance!

green69

---

### Post by HappyFeet on 2010-02-09
```
sudo apt-get install gparted ntfsprogs
```
then
```
sudo gparted
```
Choose drive from pull down menu. Then just right click drive, format and apply.

---

### Post by green69 on 2010-02-09
> **HappyFeet said:**
> ```
sudo apt-get install gparted ntfsprogs
```
then
```
sudo gparted
```
Choose drive from pull down menu. Then just right click drive, format and apply.

Thank you so much! I will give it a try!

---

