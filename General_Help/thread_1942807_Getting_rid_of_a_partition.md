---
title: "Getting rid of a partition"
date: 2012-03-18
forum: General Help
---

### Post by max00355 on 2012-03-18
I wanted to try out Linux Mint so I installed it side by side with my ubuntu installation but the problem is I don't like Linux Mint and I want to get rid of it. How do I do this?

Thanks.

---

### Post by SuaSwe on 2012-03-18
Hello max00355!

You should be able to use Gparted to delete the unwanted partition and resize your current one to take up the freed-up space. If not already installed, you can get Gparted by running the following in Terminal:

```

sudo apt-get install gparted

```

There are a lot of tutorials online about GParted - I'd recommend having a read about removing and resizing partitions before using it, and of course, you should back up all valuable data before doing anything else!

---

### Post by max00355 on 2012-03-18
> **SuaSwe said:**
> Hello max00355!

You should be able to use Gparted to delete the unwanted partition and resize your current one to take up the freed-up space. If not already installed, you can get Gparted by running the following in Terminal:

```

sudo apt-get install gparted

```

There are a lot of tutorials online about GParted - I'd recommend having a read about removing and resizing partitions before using it, and of course, you should back up all valuable data before doing anything else!
I have tried Gparted... hmm I guess I will try again. Thanks!

---

### Post by winh8r on 2012-03-18
There is some useful info here:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

to give you an overview of what is required.

Hope this helps you.

---

### Post by cottfcfan on 2012-03-18
Don't forget that if your linux Mint partition controls grub, you need to sort that out before you delete anything.
Log into your Ubuntu partition & in a terminal run:
```
sudo dpkg-reconfigure grub-pc
```
If Ubuntu already controls Grub, then just Delete your Mint Partition and run:
```
sudo update-grub
```

---

### Post by Helen McCall on 2012-03-18
Just crosses my mind to mention that if you want to delete the mint partition and grow your Ubuntu partition, you will want to run parted or gparted by booting from a cd or livecd so the partitions are not mounted. Otherwise parted will not co-operate!

---

### Post by swright007 on 2012-03-18
once you delete the appropriate partion you can always just open a terminal ( while you are still using the live CD) and issue the command 

sudo update-grub

 that should sort any grub issues.

---

### Post by swright007 on 2012-03-18
I'm sorry.. Looks like that was already mentioned.  Just try what cottfcfan said :)

---

