---
title: "Enlarging ubuntu partition"
date: 2011-01-28
forum: General Help
---

### Post by alp_oktay on 2011-01-28
Hi all, I'm new to ubuntu and this forum. This is my first message and I really need some help. I have a 500 gb harddisk and ubuntu uses only 19 gb of it. my partition style is shown in the picture. Now, I want to enlarge the ubuntu by adding 50gb free space which is under extended. Is it possible to do it without deleting ubuntu? if yes how? thanx for any help.

---

### Post by Kirboosy on 2011-01-28
You could simply Turn that Free 52 Gb into a Data partition. Just format it as ext4 and give it a name. That way you will know what it is in your file browser.

You can in theory expand your Ubuntu partition but that tends to get messy. For simplicity I would just recommend a data partition.

---

### Post by alp_oktay on 2011-01-28
The main purpose to enlarge ubuntu partition was using playonlinux to setup office programs and some games like age of empires eg. is it possible to setup them into the additional data partition?

---

### Post by Kirboosy on 2011-01-28
Hmmm I'm not sure. I know if you have setup the computer ahead of time to use the two partitions it should work. 

You might have to reinstall things then. How much free space do you have currently? If you move all your current data to the new partition you might not need to reinstall.

---

### Post by dhysk on 2011-01-28
You should be able to use the new partition, if you take that route.  However you may have to change your fstab, a text file used by linux to mount drives automaticly.

if you want to rezise things use gparted, however you always run a risk of mucking things up so do a back up first.

---

### Post by alp_oktay on 2011-01-28
Ok. thanks for the help I will talk about the results later.

---

