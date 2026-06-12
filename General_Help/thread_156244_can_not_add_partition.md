---
title: "can not add partition"
date: 2006-04-06
forum: General Help
---

### Post by kroiz on 2006-04-06
Hi 
I wanna add a partition but gparted wont let me. 
could I have reached a limit?
```

/dev/hda1 - ntfs - 49,003 - boot
/dev/hda2 - ext3 - 26,082
/dev/hda4 - ext3 - 86
/dev/hda3 - extended - 1145
     /dev/hda5 - linux-swap - 1145

``` do I have a bad design for the partitionning?

hda2 is my ubuntu.
hda4 is the boot (I think)

The problem is that my home directory is on hda2 and I want to put it on a different partition.

---

### Post by peibol on 2006-04-06
Yep, you've reached the limit, only 4 partitions, one can be extended and have N partitions inside.

---

### Post by Ramses de Norre on 2006-04-06
You should be able to make more logical partitions inside the extended one, but you'll probably need to resize and move some things around then.

---

### Post by kroiz on 2006-04-06
aaahhh, I get it. Thanks.

will you please recomand for me a size for home partition?
also when I will reinstall ubuntu, can the installer be told that this is my home and that it does not create a new home?

---

### Post by taurus on 2006-04-06
Depneding on what you do with your account, 10GB should be plenty and of course, if you have more space, make it larger.  And if you decide to install Dapper when it comes out, you can mount your /home partition and tell the installer NOT to format it.  Then, you would still have all your stuff in /home/$USER available for you, assuming you create the same username...

---

### Post by kroiz on 2006-04-07
using GParted LiveCD I resized/shrinked my big ext3 partition to 16 GiB.
which provided me with 10GiB of unallocated memory.

The problem is I could not move this free memory to the extended partition.

Right clicking on the extended partition gives me a popup menu with the "new" option disabled.

coudl it be because that the unallocated is not in the end of the disk? or should it be moved some how to the extended partition?

---

### Post by peibol on 2006-04-07
Well, your extended partition only holds your swap, you should rebuild all the hda3 partition by removing swap, deleting hda3 and then recreating it all over and then creating as many partitions as you like inside hda3.

Remember to change your fstab file to reflect the changes.

---

