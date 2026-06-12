---
title: "Start and end sector of partition"
date: 2010-06-18
forum: General Help
---

### Post by ubunxp on 2010-06-18
How to find Start and end sector of partition with sudo-command ?

/ Ubunxp

---

### Post by oldfred on 2010-06-18
You can use 

sudo fdisk -lu

or 
sudo sfdisk -luS /dev/sda

more info 
man fdisk
man sfdisk

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk

---

### Post by ubunxp on 2010-06-19
Thank you for the help!

I found the sectors

---

