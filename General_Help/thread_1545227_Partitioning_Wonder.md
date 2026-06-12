---
title: "Partitioning Wonder"
date: 2010-08-03
forum: General Help
---

### Post by Barleb on 2010-08-03
How can i organize My files , i mean i cant see inside the computer icon only File system and my cd driver , cant i make other partition for my file , and how ?

---

### Post by rawlins02 on 2010-08-03
Assuming you have a typical installation, go to Places -> Home.  Here you should see directories that were set up when you did the installation. There will likely be Pictures/, Videos/, Desktop/.  Here is where you can make other directories and place files as a user.  If you click on Places -> Computer that simply shows partitions and drives.

If you want to make a different set of partitions than currently exist you will have to get out of the boot up and re-partition using tools on the unmounted volume(s).

---

### Post by drpjkurian on 2010-08-03
If you wanna partition, logout and boot with a live cd. Use the option use ubuntu without any changes to HD. Open Gparted and partition.

---

### Post by Barleb on 2010-08-04
Well that worked perfect ;) ,

now i have little problem , the new partition is owner by root , i cant edit it , and i cant add anything to it 

how can i changer the ownership of it

---

### Post by celldweller1591 on 2010-08-04
Type > sudo nautilus in the terminal and access the partition.

---

### Post by Barleb on 2010-08-04
Well i think this could be a good temperately solution , but i want to use this new partition to store all my files , i don't this its Practical

---

### Post by WorMzy on 2010-08-04
> **celldweller1591 said:**
> Type  in the terminal and access the partition.```
sudo nautilus
```

That should be "gksu nautilus", not sudo, but it's not a good solution either way.

What you should do, OP, is make an entry for the partition in /etc/fstab.

If you post the output of
```
sudo blkid -c /dev/null
``` we may be able to help you determine what to put in the fstab entry.

---

### Post by Barleb on 2010-08-04
I can not edit on fstab

---

### Post by WorMzy on 2010-08-04
You can with ```
gksu gedit /etc/fstab
```

---

### Post by Barleb on 2010-08-04
> **celldweller1591 said:**
> Type  in the terminal and access the partition.

ok this was genius , you go through root mood and change the permission by clicking right click on the partition , then choose permission and change the owner 

thank you very much sir

---

