---
title: "How to mount root partition read-only?"
date: 2009-08-09
forum: General Help
---

### Post by Barafu Albino Cheetah on 2009-08-09
How can I mount root partition read-only so that I can fsck it and resize? Even when I boot into rescue mode, ```
 mount -o readonly,ro /dev/sda4
``` says "Cant unmount: / is busy"

---

### Post by michy99 on 2009-08-09
To fsck and resize, you don't want the partition mounted at all.

---

### Post by Rocket2DMn on 2009-08-09
If you need to resize the partition, you need to boot the system from a LiveCD.  If you don't have an Ubuntu LiveCD around, I suggest using the GParted LiveCD - [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
It is quick to download and easy to use.

As always, please backup your important data before fiddling with partitions, mostly in case you accidently do something you didn't want to.

---

### Post by blueridgedog on 2009-08-09
Also, when booting off the live CD, it will activate you hard disk's swap partition and if that is a partition you want to move or resize, you will need to turn off swap with:

```
sudo swapoff -a
```

---

### Post by Barafu Albino Cheetah on 2009-08-09
Thank you all. On Gentoo I could easily resize root partition online.

---

