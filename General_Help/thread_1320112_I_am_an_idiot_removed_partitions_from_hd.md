---
title: "I am an idiot removed partitions from hd"
date: 2009-11-08
forum: General Help
---

### Post by JigglyWiggly_ on 2009-11-08
So I was trying to dual boot with Windows 7 + ubuntu, well I shrank ubuntu successfully by booting from gparted, simple enough. Then I went to windows 7 where it said it couldn't be installed on the free space, so I used disk part and selected partition 3(the new one) and foolishly typed clean thinking that would clear the partition, except it deleted every partition including ubuntu! Is it possible to get Ubuntu back? I lost the swap file as well obviously.

---

### Post by AW36 on 2009-11-08
from my experience, no. i've destroyed all my files numerous times by playing with gparted lolz.

---

### Post by Kareeser on 2009-11-08
You're boned. Now you know the consequences of playing with fire. Sorry it had to end this way :(

---

### Post by doas777 on 2009-11-08
testdisk is your best bet if the data has not yet been overwritten. have you touched the disks since you noticed your mistake? if not then you have a good chance of sucess, but the resize operation may yet throw a monkey wrench in the works. 

try pulling down the ubuntu rescue remix, and give testdisk a try.

---

