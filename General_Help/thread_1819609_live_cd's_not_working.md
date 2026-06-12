---
title: "live cd's not working"
date: 2011-08-06
forum: General Help
---

### Post by stephenstop on 2011-08-06
I want to try out somelive cd's to find a better distro but brasero will not recognize neither memorex cd-r nor sony dvd+r,can anyone help me please

---

### Post by TeoBigusGeekus on 2011-08-07
Try from command line.
To burn a cd:
```
wodim -v dev=/dev/cdrw /path/imagename.iso
```
Replace path and imagename with their appropriate values, as well as cdrw (cd, dvd, sr0, etc.)


To burn a dvd:
```
growisofs -dvd-compat -Z /dev/cdrw=/path/imagename.iso
```
Replace were appropriate again.

---

### Post by coldraven on 2011-08-07
I have never had any luck with Brassero, just install K3B instead. It is in the Software Centre

Choose "Burn Image" from the menu to make a Live CD from an ISO file

---

