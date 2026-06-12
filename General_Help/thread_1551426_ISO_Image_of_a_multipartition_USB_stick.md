---
title: "ISO Image of a multipartition USB stick"
date: 2010-08-12
forum: General Help
---

### Post by mildenhall on 2010-08-12
I have an O2 Joggler than I have install Ubuntu Netbook 9 on. It boots off an external USB stick. I'd would like to take an ISO image of it so I don't need to completely reinstall if anything goes wrong.

The USB stick has three partitions on it. FAT, ext2, and ext3. I use an Ubuntu 10.04 laptop. How can I image the whole USB stick and not just the partitions individually please?

TIA

---

### Post by deathadder on 2010-08-12
Hi,

You can use the dd command to make a byte by byte copy of a drive. Lets assume that you're USB drive gets detected as /dev/sdc.

What you need to do is the the following command to make the copy:
```
sudo dd if=/dev/sdc of=/home/user/image
```
To restore it you'll need to run the following command:
```
sudo dd if=/home/user/image of=/dev/sdc
```
Not a ISO image, but it will allow you to completely restore the drive if you format the partitions etc :)

You'll need to check using the 'sudo fdisk -l' command to determine what device you're USB drive is, if you're not sure post the output here and we'll give you a hand. You'll also need to replace /home/user/image with the location of where you want to store the image file. It can be anywhere on your machine, since you're running the dd command as root.

---

### Post by mildenhall on 2010-08-12
Brilliant. Thanks! It turns out I was thinking too hard! My individual partitions are mounted as sdb1, sb2, and sb3. I had not thought of just using sdb for the whole memory stick. :-)

---

