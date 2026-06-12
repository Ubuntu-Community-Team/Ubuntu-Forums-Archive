---
title: "Partition Resize"
date: 2010-06-17
forum: General Help
---

### Post by damien.caci on 2010-06-17
Hi, i am currently attempting to resize my Ubuntu partition using both Vista Partition manager and Partition Wizard. I am unable to make any changes to my Ubuntu partition. I am wondering if this is something i should be worried about. I am currently trying to resize my partition to allow me to install centOS to try it out.

Any comments are welcome!

Thanks,

damien.caci

---

### Post by wojox on 2010-06-17
If you want to resize your Ubuntu partition, you need to boot from a LiveCD.

G-parted is on there to resize it for you.

---

### Post by damien.caci on 2010-06-17
Oh ok, thanks alot.

damien.caci

---

### Post by garvinrick4 on 2010-06-17
Hopefully your Ubuntu install is in an Extended partition as a logical partition and you can
put you next linux install as a logical partition. You are only allowed 4 Primary partitions on a drive and Windows needs a Primary and its Recovery needs a Primary and the Extended is a Primary so all the Linux's can be Logicals and you will not hit the Maximum amount of Primarys.

---

### Post by damien.caci on 2010-06-17
Why is it that i can't change a linux partition from within Windows? Is it designed like that?

damien.caci

---

