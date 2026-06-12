---
title: "putting pdf files together"
date: 2012-04-24
forum: General Help
---

### Post by dog-soldier on 2012-04-24
i have a couple mower manuals that are in pdf format and are in 3 different files. is there a way to put them back as 1? 
ill either be using Ubuntu 10.4 or 11.04

---

### Post by ksprasad on 2012-04-24
Hi,
 
Use pdftk.
 
sudo apt-get install pdftk
 
pdftk 1.pdf 2.pdf output 3.pdf
 
 
Regards,
ksprasad

---

