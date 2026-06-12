---
title: "How do I try to recover an openoffice document from a flash drive?"
date: 2009-07-30
forum: General Help
---

### Post by w.g.hanna on 2009-07-30
this seems like it should be simple - but is it ever?

found a website that says you can try to recover data by using scalpel, downloadable with the comand:  apt-get install scalpel

it then says to type:

scalpel /dev/sda1 -o output

with output being the name of the directory.  

this may seem rudimentary, but what do a type instead of /dev/sda1 to have it search the flash disk? what do a type in leiu of output to have it saved in my desktop folder?  

thanks!

---

### Post by TeoBigusGeekus on 2009-07-30
Mount your flash drive and see where it's mounted - let's say /media/disk
Then try
```
scalpel /media/disk -o ~/Desktop
```
Post us the results.

---

