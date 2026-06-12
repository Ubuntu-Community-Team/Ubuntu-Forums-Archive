---
title: "UBUNTU Not using HDD space"
date: 2012-09-19
forum: General Help
---

### Post by shaqsalazar on 2012-09-19
Hi, i just install ubuntu on a 250 gb partition HDD(actually size 750 GB) but ubuntu will only use 18 gb, wont use anymore. On system moniter is says 226.6 GB free....Can someone tell me y that is? And how to make it use the full 250 GB

---

### Post by twipley on 2012-09-19
Does a specific error message appears telling you that there is no more free space? Detailed, typo-free verbose would not hurt...

---

### Post by oldfred on 2012-09-19
Post these from terminal:

sudo fdisk -lu

sudo parted /dev/sda unit s print

df -h

---

