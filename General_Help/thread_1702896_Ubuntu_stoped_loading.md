---
title: "Ubuntu stoped loading"
date: 2011-03-08
forum: General Help
---

### Post by leguitos on 2011-03-08
.

---

### Post by blueridgedog on 2011-03-08
I would boot on a LiveCD and run fsck on your partition:

```
sudo fsck /dev/sda1
```

Replace /dev/sda1 with the path of your actual root partition.  

You can post the output of 

```
sudo fdisk -l
```

If you want help identifying the partition.  Note that is a lower case "L" after fdisk.

---

