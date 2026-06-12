---
title: "HELP..adding more space to Ubuntu partition"
date: 2010-02-10
forum: General Help
---

### Post by D3mon_Spawn on 2010-02-10
When I first decided I wanted to start using Ubuntu, I was using Windows Vista. I created a separate partition by shrinking a portion of my current windows partitions to 60g of free space. I then booting my computer with the Ubuntu live CD and installed it under that 60g of free space. (I dual boot now and have been happy ever since:p). I guess my question is if I boot back into windows and format the 60g partition, can I shrink more of my windows partition and allocate more of it to the 60g part? I'm only asking this since I would like more space when the newer Ubuntu version comes out. I wasn't sure if by doing this GRUB will get deleted as well and mess up my computer.

---

### Post by plucky on 2010-02-11
> I guess my question is if I boot back into windows and format the 60g partition, can I shrink more of my windows partition and allocate more of it to the 60g part?

Do you actually mean format? That would wipe the partition.

If you do mean format,just select the **use un-allocated space** when you do the install and it will use the increased space.

**Use windows vista disk management to shrink the vista partition.**

Are you going to do a clean install or an upgrade from Karmic to Lucid?

Do you have a separate /home partition?

The Ubuntu Live CD can be used to increase the size of a partition,but a partition can only be re-sized if the un-allocated space is at the rear of the partition.

As the un-allocated space will be in front of the partition,you will have to move the front of the partition and all its data into the un-allocated space.This can take a very long time depending on the amount of data to be moved.You can then increase the size of the partition as the un-allocated space will have moved to the rear.

When a partition size is increased,the UUID of the partition is changed,which can cause grub boot and mounting problems,check out the "Tutorial and tips" section for Howto's update grub and fstab to take this into account.

Good Luck

---

### Post by drs305 on 2010-02-11
Here is the link to a guide on expanding an Ubuntu / partition. It was written in response to a bug in the Jaunty installer. The actual instructions and tips start about half way through the post.

[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by D3mon_Spawn on 2010-02-11
> **plucky said:**
> Do you actually mean format? That would wipe the partition.

If you do mean format,just select the **use un-allocated space** when you do the install and it will use the increased space.

**Use windows vista disk management to shrink the vista partition.**

Are you going to do a clean install or an upgrade from Karmic to Lucid?

Do you have a separate /home partition?

The Ubuntu Live CD can be used to increase the size of a partition,but a partition can only be re-sized if the un-allocated space is at the rear of the partition.

As the un-allocated space will be in front of the partition,you will have to move the front of the partition and all its data into the un-allocated space.This can take a very long time depending on the amount of data to be moved.You can then increase the size of the partition as the un-allocated space will have moved to the rear.

When a partition size is increased,the UUID of the partition is changed,which can cause grub boot and mounting problems,check out the "Tutorial and tips" section for Howto's update grub and fstab to take this into account.

Good Luck

Yes I want to format and do a fresh install. I don't have a separate home partition, everything is on the 60g portion.

---

### Post by audiomick on 2010-02-11
I would use the Vista tool to shrink the windows partition, based on repeated advice to do so that I have seen here. Further to that, it is often recommended to clean out the windows partition thoroughly first, and de-fragment it a couple of times. After shrinking, start it a couple of times an let it do any file checking it wants to do.

When windows is happy, you can go on to the Ubuntu install. I would just go into the installer and set up the paritions using the "manual partitionin" option, including a seperate /home partition. I have also seen a few posts suggesting using the gparted CD or gparted from the live install to do the partitioning for Ubuntu before the install. I can't say for sure what is better.

---

### Post by D3mon_Spawn on 2010-02-11
> **drs305 said:**
> Here is the link to a guide on expanding an Ubuntu / partition. It was written in response to a bug in the Jaunty installer. The actual instructions and tips start about half way through the post.

[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

thanks for this link, i understand this part already. My issue is with GRUB; what will happen if I do a fresh install over the new expanded Ubuntu partition?




> check out the "Tutorial and tips" section for Howto's update grub and fstab to take this into account. 

couldnt find this btw, can you post a link please O:)O:)

---

### Post by audiomick on 2010-02-11
If you do a fresh install, grub should take care of itself. If you remove the Ubuntu partitions and try and reboot before you have re-installed, you will probably get a grub error, so leave the ubuntu alone until you are ready to go on with the install.

Info on grub 2, which is what is installed with 9.10 here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

