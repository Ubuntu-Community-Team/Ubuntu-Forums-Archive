---
title: "can I restore a ddrescue img file the same way I restore dd img?"
date: 2012-05-04
forum: General Help
---

### Post by deckoff on 2012-05-04
I bought a new PC, which comes with Win7 pre-installed. Just in case (warranty, blah) I want to back-up the whole ssd.
[LIST=1]
[*] I tried with Clonezilla, but Clonezilla reported that the image is not checkable
[*]I tried to img with dd, but dd worked whole night ( for 128gb ssd) and never finished
[*]I am doing the same with ddrescue at the moment(it report progress). 
[/LIST]
```
ddrescure /dev/sda /blah/lenovo.img
```
Can I restore the img file produced to the hard-disc again. Usually, I can go with 
```
dd if=blah/lenovo.img of=/dev/sda
```
and this should revert changes back. 
Can I do the same with ddrescue-img, with dd or ddrescure?

---

