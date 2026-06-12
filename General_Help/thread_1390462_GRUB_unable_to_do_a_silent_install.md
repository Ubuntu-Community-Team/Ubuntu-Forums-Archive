---
title: "GRUB unable to do a silent install"
date: 2010-01-25
forum: General Help
---

### Post by viddect on 2010-01-25
I am trying to install grub through a script but I cannot do it. 

I have a working script that deletes any existing partitions runs fdisk and sets up a 100M partition for grub but when i call grub I cannot get it to install grub. 

I have a pxe automation enviroment I am doing this in. 

here is the script I have so far

#!/bin/sh
DRIVE="/dev/sda" # change this to your hard drive you wanna erase
PART="/dev/sda1"
 
dd if=/dev/zero bs=512 count=1024 of=$DRIVE # erase the first 1megabyte
I fail the 2nd script... grub never installs. any help would be good. 
##################1st script#################
fdisk $DRIVE << EOF
n
p
1
25
+100M
w
EOF

mke2fs $PART
 
###################2nd script#######################
#!/bin/sh

mkdir /mnt/g
mount -t ext2 /dev/sda1 /mnt/g
mkdir /mnt/g/boot
mkdir /mnt/g/boot/grub
cp /boot/grub/stage1 /boot/grub/stage2 /mnt/g/boot/grub

grub --batch --device-map=/dev/sda <<EOF
device (hd0) /dev/sda1
root (hd0,0)
setup (hd0)
quit
EOF

---

