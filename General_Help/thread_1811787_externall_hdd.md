---
title: "externall hdd"
date: 2011-07-25
forum: General Help
---

### Post by mr.farenheit on 2011-07-25
i have a 1 tb external hard drive that i use for backing up my movies and music. i just did a clean install of ubuntu 10.04 64 bit. for some reason after using the drive, when i choose to safely remove, it locks up my computer forcing me to do a hard boot. also, it is formatted to ntfs because for some reason linux wouldn't recognize the drive before it was formatted and when i tried to format it to another file system it would read an error.

---

### Post by galvatron408 on 2011-07-25
ok, formatting means losing all your data but if you want, you can do this...

sudo fdisk $your_usb_dev (for example /dev/sdx)

(make sure you see the correct size; you don't want to fdisk your local drive)

press p to print the partition table

then, when happy, press d to delete the partition table
then, press n to create a linux partition
then, press w to write the changes and exit

at the command prompt, type:
sudo mke2fs -T ext4 -m 0 $your_usb_partition (for example /dev/sdx1)

then, mount your newly created partition:
sudo mount $your_usb_partition /somedir/somelocation/

---

### Post by claracc on 2011-07-26
> i have a 1 tb external hard drive that i use for backing up my movies and music. i just did a clean install of ubuntu 10.04 64 bit. for some reason after using the drive, when i choose to safely remove, it locks up my computer forcing me to do a hard boot

It is a bug related to kernel 2.6.32-33. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

What works for me is to umount the usb hdd from comand line

---

### Post by mr.farenheit on 2011-07-27
i'll try unmounting from the terminal. thanks gang!

---

