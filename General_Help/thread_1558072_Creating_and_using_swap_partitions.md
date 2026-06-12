---
title: "Creating and using swap partitions ?"
date: 2010-08-21
forum: General Help
---

### Post by MindCalamity on 2010-08-21
Ok, so I removed my swap partition, including all the other partitions on my hard drive except the ubuntu one, now how do I create a new swap ?

---

### Post by Vishnu V on 2010-08-22
Use gparted to create partition.
Right click on free space and select new set the size and select linux swap as file system and apply
For auto mounting swap
open terminal
```
sudo gedit /etc/fstab
add the following line
UUID=**<uuid of swap partition>** none            swap    sw              0       0

```
now save and exit
to know <uuid of swap partition>
right click on swap partition and select information
my fstab entry for swap is shown below
```

UUID=7133da8a-1ac7-4c59-8f0b-2c228b330365 none            swap    sw              0       0


```

---

