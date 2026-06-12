---
title: "Problems with HDD"
date: 2012-02-06
forum: General Help
---

### Post by vollager on 2012-02-06
Hi tere, im trying to install Ubuntu 11.04, 11.10, 10.04, backtrack, mint and i have the same thing, in all distros in the part of selection of the HDD dont show me anything, is strange because in the command fdisk -l i have the disk, so the SO detect my HDD but the installer dont!, i cant find the solution, i format the HDD with partition magic, i check the table with partition doctor and all is fine!!! and one curios thing is when i put a pendrive that is detected in the installer, so i dont know what to do, please heeeelp!!

---

### Post by vollager on 2012-02-06
Well i solved it, i put in a terminal:

```
# dmraid -E -r /dev/sda
```

then asked me to remove the raid data and voila!! thanks anyway...

---

