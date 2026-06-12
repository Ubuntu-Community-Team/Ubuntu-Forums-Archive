---
title: "Ubuntu and Clonezilla"
date: 2010-07-09
forum: General Help
---

### Post by zeta_immersion on 2010-07-09
I have installed Ubuntu and clonezilla and 2x250Gb hard drives. 

I have formatted the system as "Guided – Use entire disk and set up LVM" so it created its own partition table and what not (on drive 0)

Now for drive 1 I did the following:

fdisk /dev/sdc (formatted it 8e  for LVM)
pvcreate /dev/sdc1
vgextend clone-server /dev/sdb1

and everything went ok, now my question is ... does the server see I big partition 466GB? or still only 240GB (first drive)?
moreover .. if I try to 
umount /home/ 
lvextend -L100G /dev/clone-server/home
resize2fs /dev/clone-server/home

it does not work saying /home/ is not mounted (though I can clearly save to it and access it)

also, would it be possible to know what files I have saved on the second drive? ... I do not want to mess anything up by adding it to the first drive now that I have 2 images on it)

Thank you

---

### Post by zeta_immersion on 2010-07-10
So no one is familiar with formatting hard drives and (re)configuring hard disk space?

---

