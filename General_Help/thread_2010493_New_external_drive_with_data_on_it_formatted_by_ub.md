---
title: "New external drive with data on it formatted by ubuntu (does not work anymore)"
date: 2012-06-25
forum: General Help
---

### Post by shimana on 2012-06-25
Hey guys.

I have given my problem in the heading actually but to be more precise here it is: 

I've bought a WD external drive 2TB, and I've put 1 tb of data in it, all working smoothly. and after some time I've installed ubuntu on my netbook and I wanted to get some of the data from the external to my netbook. That's when it got bad.

As far as I can understand the external drive was not formatted when I put the data in it (although I could see the storage space and keep on putting data in it) and when I inserted the external in ubuntu, it formatted the drive as it seems fit. When I plug my external to my pc now and go disk management, it gives me 5 partitions, 2 with 1 tb of data on them but cannot access these partitions neither in windows or in ubuntu. (Also it takes quite some time for the computer to recognize the disk and stuff)

Lately, after futile attempts to solve the problem, I've been considering even losing 1 tb of data and making a fresh start but windows does not even let me format the disk for some reason.

Now my questions are, 

Can I save the data in the disk although I've messed up with some partitions created by ubuntu. 

If I cannot do this, then can I at least format the drive in one of the windows formatting "formats".

Looking forward to your replies.

---

### Post by hansdown on 2012-06-25
Welcome to the forum,shimana.

Do you have a "live" ubuntu disk to use?

Running the live disk can help.

Post back, and we'll try to help.

---

### Post by oldfred on 2012-06-25
Ubuntu cannot automatically format a drive, unless you actually installed Ubuntu to the drive. How was it formated before?

It is normal that Windows will not see Linux formated partitions, but often external drives are preformatted with FAT32 which is not a good format to use or not formated and users write data into unformated space. If you want to share data with Windows NTFS is a better format.

From Ubuntu liveCD or your install.

```
sudo fdisk -lu
```

Click on any partitions from the external in Nautilus to mount them as this only shows mounted partitions

```
df -H
```

---

