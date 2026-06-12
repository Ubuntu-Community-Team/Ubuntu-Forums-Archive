---
title: "Just confirming, is this correct?"
date: 2012-07-28
forum: General Help
---

### Post by jonnyboysmithy on 2012-07-28
I backed up using the command 
```
gksudo dd bs=15M if=/dev/sda5 conv=sync,noerror | gzip -9 > /home/myusername/.System-Root-Partition-Image.img.gz
```So to restore I would have to :
```
sudo dd if=/media/filelocation.img.gz of=/dev/sda1
```
Correct?

---

### Post by jonnyboysmithy on 2012-07-30
Solved! [http://ubuntuforums.org/showthread.php?p=12138722#post12138722](http://ubuntuforums.org/showthread.php?p=12138722#post12138722)

---

