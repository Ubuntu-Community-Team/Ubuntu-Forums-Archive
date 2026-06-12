---
title: "How do I reinstall Ubuntu..."
date: 2011-05-03
forum: General Help
---

### Post by brianlen on 2011-05-03
How do I reinstall Ubuntu without wiping my personal data files?

---

### Post by Quackers on 2011-05-03
You can't really do that unless you installed Ubuntu with a separate home partition afaik

---

### Post by brianlen on 2011-05-03
> **Quackers said:**
> You can't really do that unless you installed Ubuntu with a separate home partition afaik

Okay, how do I create a separate home partition when installing Ubuntu?

---

### Post by Quackers on 2011-05-03
You create a second partition of type ext4 and make the mount point "/home" instead of "/" for root.

---

### Post by Rubi1200 on 2011-05-03
Like this:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I actually recommend you create 3 partitions ahead of time;

1. swap partition, should be about 1.5x the installed RAM e.g. if you have 1GB RAM, swap would be 2GB

2. root / partition of 10-20GB

3. the rest for the /home partition

Obviously, you can adjust according to how much space you have on the drive.

Once installed, you can then reinstall in the future by using manual partitioning, telling the installer to format root but NOT the home partition.

Does this make sense? Feel free to ask questions if it does not.

---

### Post by brianlen on 2011-05-03
> **Rubi1200 said:**
> Like this:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I actually recommend you create 3 partitions ahead of time;

1. swap partition, should be about 1.5x the installed RAM e.g. if you have 1GB RAM, swap would be 2GB

2. root / partition of 10-20GB

3. the rest for the /home partition

Obviously, you can adjust according to how much space you have on the drive.

Once installed, you can then reinstall in the future by using manual partitioning, telling the installer to format root but NOT the home partition.

Does this make sense? Feel free to ask questions if it does not.

Okay, should all partitions be of type ext4?
You say 1.5x the install RAM but having a swap 2GB is 2.0x 1GB, so that doesn't make sense.
And for the "device boot loader" is that GRUB? and which partition do I install it on?

---

### Post by dragonfly41 on 2011-05-03
Following the advice I've got "/" and "/home" mounted in two partitions .. plus an ntfs partition for sharing with Windows Vista.

but I've noticed that some users create separate partitions for /boot (Grub) and /etc    (e.g. I have apache and tomcat installed which appear there)

So how "fine grain" should partitioning be with apache + php5 + mysql + tomcat6 .. etc.  installed?

---

### Post by brianlen on 2011-05-03
> **Rubi1200 said:**
> Like this:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

swap partition, should be about 1.5x the installed RAM e.g. if you have 1GB RAM, swap would be 2GB


The link to the guide says that if I have 1 or 2 GB of RAM that I wouldn't need a swap partition. I have 4 GB of RAM, do I still need a swap partition?

---

### Post by wilee-nilee on 2011-05-03
> **dragonfly41 said:**
> Following the advice I've got "/" and "/home" mounted in two partitions .. plus an ntfs partition for sharing with Windows Vista.

but I've noticed that some users create separate partitions for /boot (Grub) and /etc    (e.g. I have apache and tomcat installed which appear there)

So how "fine grain" should partitioning be with apache + php5 + mysql + tomcat6 .. etc.  installed?

A actual boot partition instead of just the mbr is rarely needed or advised. There are more exotic set-ups that will use a partition but not very common. Servers may be different as well, but a regular install with a regular mbr set-up would only need it if the user wanted it.

---

### Post by Quackers on 2011-05-03
Grub doesn't go in a partition, normally. It goes to the mbr of the hard drive which is usually /dev/sda. The only time this really changes is if there is more than one hard drive on the system. Then it may be necessary to change the destination of grub.

---

### Post by Rubi1200 on 2011-05-03
> **brianlen said:**
> The link to the guide says that if I have 1 or 2 GB of RAM that I wouldn't need a swap partition. I have 4 GB of RAM, do I still need a swap partition?
For more information about swap, read here please:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by brianlen on 2011-05-03
> **Quackers said:**
> Grub doesn't go in a partition, normally. It goes to the mbr of the hard drive which is usually /dev/sda. The only time this really changes is if there is more than one hard drive on the system. Then it may be necessary to change the destination of grub.

Yeah, I have more than one hard drive, so which partition does Grub go on? Root?

---

### Post by Quackers on 2011-05-03
No, you're not grasping this are you :-)
It doesn't go in a partition - it goes in the mbr of the hard drive - the Ubuntu hard drive. For example /dev/sdb or /dev/sdc, depending on the designation of the drive Ubuntu is on. Check with gparted.

---

### Post by brianlen on 2011-05-03
> **Quackers said:**
> No, you're not grasping this are you :-)
It doesn't go in a partition - it goes in the mbr of the hard drive - the Ubuntu hard drive. For example /dev/sdb or /dev/sdc, depending on the designation of the drive Ubuntu is on. Check with gparted.

But won't that replace my Windows 7 boot loader?

---

### Post by Quackers on 2011-05-03
If Windows is on the same drive, yes. That's what it does. You then run sudo update-grub from within Ubuntu and the Windows Loader is found and you can then boot into Windows from the grub menu.
If Windows is not on the same drive as Ubuntu you make the Ubuntu drive bootable before the Windows drive in the bios.

---

