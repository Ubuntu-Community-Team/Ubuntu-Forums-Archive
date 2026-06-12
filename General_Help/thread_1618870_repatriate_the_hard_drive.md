---
title: "repatriate the hard drive"
date: 2010-11-11
forum: General Help
---

### Post by oren tal on 2010-11-11
I have installed ubuntu and now I want to install centos as a dual boot.

For this I need to repatriate the hard disk, how do I do it?

Can I do it from with in the ubuntu?

Thanks.

---

### Post by 3Miro on 2010-11-11
You will need to use the LiveCD. Boot from the Ubuntu LiveCD and then use Gparted (I think it is in System -> Admin -> Gparted) to "resize" your partition to make room for CentOS. 

MAKE SURE YOU BACKUP ALL IMPORTANT INFORMATION FROM YOUR HDD. If something goes wrong (i.e. you delete a partition by accident or resize fails) then you can lose all of your files.

---

### Post by oren tal on 2010-11-11
> **3Miro said:**
> You will need to use the LiveCD. Boot from the Ubuntu LiveCD and then use Gparted (I think it is in System -> Admin -> Gparted) to "resize" your partition to make room for CentOS. 

MAKE SURE YOU BACKUP ALL IMPORTANT INFORMATION FROM YOUR HDD. If something goes wrong (i.e. you delete a partition by accident or resize fails) then you can lose all of your files.
thanks.

---

