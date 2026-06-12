---
title: "Accessing 2nd HDD?"
date: 2010-02-19
forum: General Help
---

### Post by black28 on 2010-02-19
Heys, my Desktop only has a 60GB HDD which i am running Linux Xuuntu on...I just found a 40GB HDD that i install into the desktop as well. what i really wanna do with it is wipe it clean and then format it to be accessible from my Linux Distro like "Extra Memory" for storing things like music etc. i'm having trouble doing this. it reads in Gparted but not quite sure what i need to do to do this. can someone assist me please?

---

### Post by joeknoodle on 2010-02-19
I'm an amateur, so use caution. Read and understand all diirections before applying, and make necessary backups.

In GParted do:

1- In the upper right corner there is a box that shows the current HD you're working on. Make sure it shows the HD you wish to format.

2- *You may or may not have to erase the partition(s), if so, select one at a time and erase / delete.

3- Upon removing all partitions, you can start building new partitions.

4- Right click and tell it what type of partition you want - ext3, ext4, size, mount point, etc.

5- When you're satisfied click apply.

*If only one partition, you may be able to just overwrite that partition information.

---

### Post by undecim on 2010-02-19
I'm a little fuzzy on the specifics of gparted, but I think joeknoodle is correct. Just double check that first step, and make sure that you are using the correct drive. You don't want to end up formatting your main hard drive! (it's really not fun to do, trust me)

Also, for the partition type, use ext4, unless you will be using this with a windows system as well.

---

