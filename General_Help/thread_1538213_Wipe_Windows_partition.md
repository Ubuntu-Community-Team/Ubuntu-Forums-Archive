---
title: "Wipe Windows partition"
date: 2010-07-24
forum: General Help
---

### Post by altjx on 2010-07-24
Anyone can show/tell or direct me to a guide to removing Windows 7 off my other partition? I'd just prefer to have Ubuntu 10.4 on the entire HD instead of dual booting. I came here so I didn't have to reinstall and wipe the entire HD to do so. Pretty sure there's a way to wipe 7 off the other side and update GRUB to only detect ubuntu.

---

### Post by geoffjay on 2010-07-24
Assuming that you've only got one drive in your setup you would do

$ sudo fdisk /dev/sda
p (to show table)
d (to delete a partition)
(pick partition # to delete)
w (to write the table)

If you're not comfortable with the command line you might want to try gparted instead, I've never used it so I can't offer any suggestions there.

Edit:
to update grub you need to run
$ sudo update-grub

---

### Post by altjx on 2010-07-24
I used GParted to delete the partition, but now I can't extend the extended partition into the unallocated space Windows 7 took up. When I rebooted, Windows 7 was still in the GRUB list. How do I update the GRUB menu and extend the extended partition? Even booted from the Ubuntu CD but couldn't extend. Was a greyed out option.

---

### Post by altjx on 2010-07-24
K, I updated the GRUB menu. Now just trying out how to extend the extended partition.

---

### Post by geoffjay on 2010-07-24
I may have edited the original post before you replied but you would do as suggested:

$ sudo update-grub

I'm not completely sure about resizing your partition but what you might want to do is create a separate data or home partition, that way if you mess up your system and need to reinstall you don't have to worry about the other partition.

To do that,

$ sudo fdisk /dev/sda
n (to create new partition)
p or e (up to you)
(pick a number)
(press enter twice to make the partition the size of the remaining space)
w (to write table)
$ sudo mkfs.ext3 /dev/sda# (# is whatever you chose previously)
ext3 can be changed to whatever you like, ext4, reiserfs, xfs, etc.

$ sudo gedit /etc/fstab
add the new partition, eg

/dev/sda# /mnt/data ext3 defaults 0 2

again, # is from previous choice, /mnt/data can be changed to whatever you like, and ext3 has to match the choice made earlier with mkfs.

$ sudo mount /mnt/data

---

### Post by altjx on 2010-07-24
booted from gparted live cd and got it done. it's taking about an hour but gets the job done

---

