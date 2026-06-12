---
title: "gparted cannot resize external hard disk"
date: 2012-03-04
forum: General Help
---

### Post by Diomedes1905 on 2012-03-04
Hi all, I have this same problem with GParted but still can not solve it. I've done what I read in this post [http://ubuntuforums.org/showthread.php?p=9149220](http://ubuntuforums.org/showthread.php?p=9149220) , but still can not get good results.

---

### Post by kazztan0325 on 2012-03-04
Hi Diomedes1905,

It seems a package 'e2fsprogs' has not installed yet or it had installed but has broken...
Please check it first.

---

### Post by Diomedes1905 on 2012-03-04
Nope, everythings its ok, i use 

```
sudo dpkg --configure -a
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> **kazztan0325 said:**
> Hi Diomedes1905,

It seems a package 'e2fsprogs' has not installed yet or it had installed but has broken...
Please check it first.

---

### Post by Paqman on 2012-03-04
Is there data on the drive that you want top preserve? If not, just delete the partition and start from scratch.

---

### Post by kazztan0325 on 2012-03-04
Hmm..., then why does the Warning say "The following list of software packages is required for ext4 file system support: e2fsprogs v1.41+." at last sentence...
I also don't know why though.

---

### Post by Diomedes1905 on 2012-03-04
Yes i have 300GB of data. > **Paqman said:**
> Is there data on the drive that you want top preserve? If not, just delete the partition and start from scratch.

---

