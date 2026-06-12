---
title: "uninstall OS"
date: 2010-07-06
forum: General Help
---

### Post by Skyhighnemo on 2010-07-06
How do I remove 8.04 of my notebook so I can do a new install in 10.04?

Sky

---

### Post by ScarletWyvern on 2010-07-06
You can just install over it.

Granted, you'll lose all your data.

---

### Post by Skyhighnemo on 2010-07-06
The problem there is that it still leaves reminences behind of old OS..  I would like to compltely uninstall 8.04 and install new 10.04 notebook.  I was thinking about buying a new drive, but I just bought a new one less than 30 days ago and cloned the old 8.04 on to it.  So now I want to completely uninstall the 8.04 OS and do a new install of 10.04 notebook without any old OS remains.  Surely there must be way to completely uninstall the old OS.. 

Sky

---

### Post by Firedrake445 on 2010-07-06
Could you use a live cd to totally delete all partitions and format the volume with gparted or something?

---

### Post by Skyhighnemo on 2010-07-06
OK.. I will try that.. 

Thanks, 

Sky

---

### Post by Serpher on 2010-07-06
Just boot your 10.04 CD and install the OS using the option to use all of the hardrive, or if you have other partitions you don't want touched just the partition of your root directory assuming you don't have /home and other things in other directories. If this isn't helpful post the output of:

```
fdisk -l
```

---

### Post by ScarletWyvern on 2010-07-06
> **Skyhighnemo said:**
> The problem there is that it still leaves reminences behind of old OS.. 
No it won't...

By install over it, I mean use a LiveCD to install, and opt to use the entire partition/disk.

---

### Post by arpanaut on 2010-07-06
> The problem there is that it still leaves reminences behind of old OS..

Wrong, If you format the partition that the 8.04 is installed on during the installation on 10.04 and choose to not to retain any data. It will have the same effect as formating the partition before hand.  I don't know where you got that information but someone is blowing smoke up your you know what.

Formating is formating.. no data will be preserved.

---

### Post by Skyhighnemo on 2010-07-09
No one has said anything about formatting.. only removing old OS.. from the current partition.  What was done before was the OS was loaded over the top as an update..  not formatted..  
Sky,

---

