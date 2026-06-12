---
title: "Help Partitions and/or Virtual Enviroment"
date: 2010-08-10
forum: General Help
---

### Post by adwhitenc on 2010-08-10
Any help will be appreciated, feel free to ask questions to help with the solution.

I am a 5 year user and I recently obtained a Sony Vaio with 2 gb of memory, a 160 GB hard drive, and an Intel dual-core processor. I will soon be installing ubuntu but also want to run windows XP under it through a virtual environment (probably virtual box). 

My questions are:

1. After creating the 2gb swap drive i will have approximately 158 GB of space to partition between the two systems. How should I partition for the two systems(ubuntu and windows XP) and should i create a shared partition.

2. I had a Compaq laptop before and virtual-box didn't work well. Do you have any suggestions for another virtual environment program?


Additional Information: On my current computer, I am using 10 GB in my ubuntu system.


Thank you for your help.

---

### Post by labinnsw on 2010-08-11
If you are dual booting, keep Ubuntu to 70 Gb or less. For some reason XP malfunctions if the Ubuntu partition is larger. There would be no point in sharing any partition. Ubuntu will read the Windows partition. The opposite is not possible. Since only one system will be on at a time, Windows would not be able to read your shared linux partition.

If you are using only the virtual option, make your guest virtual disk 20 Gb or More. This should allow ample space for software installation. I would also recommend storing it in separate partition. e.g. My PC has 3 partitions, System, Backup, and Storage. System gets backed up regularly, Storage gets backed up occasionally (when I change something significant like adding a new virtual disk or a software download) and Backup is where the Backups are stored. It is also a separate disk. Mine is internal but the best advice is for it to be external. Sharing a directory on the host should be sufficient.

The other free and Open virtual environment I tried was QEMU. It has some advantages, but I found 2 significant drawbacks. It tended to be slow and the learning curve is comparatively steep. I have not used it for a while now.

---

### Post by howefield on 2010-08-11
> **adwhitenc said:**
> After creating the 2gb swap drive i will have approximately 158 GB of space

Most likely you won't have much more than about 150 after creating the swap. 160 gigabyte drive will probably give you about 152-154 of usable space to start with.

> How should I partition for the two systems(ubuntu and windows XP) and should i create a shared partition.

I'm not clear on what you want, if you have Ubuntu on your machine with Windows virtualised, you won't need a separate partition on your hard drive for a virtual windows install, as it will be installed as a virtual drive in your existing Ubuntu install. Hope that makes sense, probably doesn't read that well...

Performance wise, it's best to store virtual machine on separate disk to your operating system.


> Do you have any suggestions for another virtual environment program?

There is a free edition of VMWare, long time since I used it so don't know how good it is. Virtualbox has served me well enough, using the PUEL version downloaded from the virtualbox website.

---

### Post by adwhitenc on 2010-08-12
Thank you both very much for your help.

---

