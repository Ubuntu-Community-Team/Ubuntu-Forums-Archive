---
title: "I need help with partitioning and dual booting"
date: 2011-05-16
forum: General Help
---

### Post by ChaosChris2009 on 2011-05-16
I'm going to install and dualboot pinguy os with my current install of Ubuntu 11.04

I'm stuck on the advanced partitioning part, how do I give Pinguy a 30GB hard drive?

And does this involve creating a new partition table?

Please help

---

### Post by ChaosChris2009 on 2011-05-16
I don't mean to bump, but I really need help

I'm new partitioning and don't want to mess anything up

---

### Post by CrushingYourHead on 2011-05-16
Are you trying to say that your HD has only 1 partition (Ubuntu) and you would like to add another partition to the back end of the drive to install the second OS?

I think you need to resize the original first before performing the install. I've done this before by using a live disk like Parted Magic or Hiren Boot Disk.

---

### Post by eltommo on 2011-05-16
you can do it fine with the ubuntu live cd too by running gparted. you MIGHT also be able to resize a partition by going into single user mode but im not really sure on that.

---

### Post by Cfhs_1 on 2011-05-16
Yea, pop in your ubuntu 11.04 disc and open gparted. Click on your ubuntu partition and resize it to about 30GB smaller. Next create a new ext4 partition to fill the empty space. After that right click on the net ext4 partition, and click "Manage flags" Tick the box next to "BOOT" and close that. Then start the other distro's installer, and install to the newly created partition. This should be pretty straight forward. If you get stuck let us know. Also, when setting the boot flag, you have to APPLY all of the settings for the partition resize, and creation before it will let you manage the flags.

---

### Post by ChaosChris2009 on 2011-05-17
> **Cfhs_1 said:**
> Yea, pop in your ubuntu 11.04 disc and open gparted. Click on your ubuntu partition and resize it to about 30GB smaller. Next create a new ext4 partition to fill the empty space. After that right click on the net ext4 partition, and click "Manage flags" Tick the box next to "BOOT" and close that. Then start the other distro's installer, and install to the newly created partition. This should be pretty straight forward. If you get stuck let us know. Also, when setting the boot flag, you have to APPLY all of the settings for the partition resize, and creation before it will let you manage the flags.

I just want to make sure I have this right.... My Ubuntu partition is the biggest one which is 231GB 

and I create the new partition table under that one right?

or am I supposed to resize it?

Theres 3 boxes when I go to resize

Look at the second attachment, tell me which box I put the 30GB on

---

### Post by eltommo on 2011-05-17
resize it. you can use the black arrow on the right if you want. after doing this, you can right click on the new empty space and format it to ext4 or whatever you want. the changes will only be applied when you press the apply button, not straight away. make sure you back up anything really critical first though, just in case.

---

### Post by Cfhs_1 on 2011-05-17
Yep, just resize it. Don't forget to right click on the new partition after you have applied the settings and enable the boot flag. I'm not sure if installing an operating system to a blank ext4 partition does this automatically or not, best be on the safe side though.

---

### Post by eltommo on 2011-05-17
> **Cfhs_1 said:**
> Yep, just resize it. Don't forget to right click on the new partition after you have applied the settings and enable the boot flag. I'm not sure if installing an operating system to a blank ext4 partition does this automatically or not, best be on the safe side though.

does the boot flag still matter? I thought it was a leftover from the dark ages.

---

### Post by Cfhs_1 on 2011-05-17
I thought the same thing, but the last time I tried to install puppy linux I forgot to set the boot flag and it wouldn't boot. Better safe than sorry in my opinion. It will save you from having to boot the live CD again just to fix it.

---

### Post by oldfred on 2011-05-17
Grub does not use boot flag. Windows & Lilo use boot flag. And windows has to have the boot flag on a primary partition.

There also are some BIOS (Intel for one) that seem to assume windows and you get a BIOS error (before grub even starts) and cannot boot unless you have a boot flag on a primary partition.

So I always suggest putting a boot flag on a primary partition.

---

### Post by Cfhs_1 on 2011-05-17
> **oldfred said:**
> Grub does not use boot flag. Windows & Lilo use boot flag. And windows has to have the boot flag on a primary partition.

There also are some BIOS (Intel for one) that seem to assume windows and you get a BIOS error (before grub even starts) and cannot boot unless you have a boot flag on a primary partition.

So I always suggest putting a boot flag on a primary partition.

Ah, so that's why Puppy needed a boot flag. :)

---

