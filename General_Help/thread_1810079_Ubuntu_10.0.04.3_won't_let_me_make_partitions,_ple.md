---
title: "Ubuntu 10.0.04.3 won't let me make partitions, please fix it"
date: 2011-07-22
forum: General Help
---

### Post by Lukasz Tarkowski on 2011-07-22
Ubuntu 10.0.04.3 won't let me make partitions, please fix it

---

### Post by Quackers on 2011-07-22
Might need more info than that :-)
Why not? What is it saying?

---

### Post by Lukasz Tarkowski on 2011-07-22
I have free space no volume, and when I click on it can't resize, can't mount, if I create Linux EXT 3 and Linux Swap in Windows, the HDD SDÀ`S disappear, go blank, I am trying to install at the boot cd

---

### Post by Quackers on 2011-07-22
In what? Gparted? The Ubuntu installer?

---

### Post by Lukasz Tarkowski on 2011-07-22
In the Ubuntu installer won't let me create partitions and mount,  I tried making partitions in Acronis Disk Director wouldn't help

---

### Post by Quackers on 2011-07-22
Does it say that it is unallocated space in the installer?
If you double-click on that unallocated space does a new window open up?

---

### Post by Lukasz Tarkowski on 2011-07-22
If I right click says Revert, i will try your idea brb

---

### Post by mikejonesey on 2011-07-22
don't know your experience level, are you aware of hardware limitations like max 4 primary partitions?

---

### Post by Lukasz Tarkowski on 2011-07-22
It said partition was unusable.

---

### Post by Quackers on 2011-07-22
What partition is unusable? Is there a partition shown? ie sda1,sda2 etc.
Is this a brand new disc or has it been used in a different pc?
Has the disc been formatted? If so, how and was it mbr or GPT?

---

### Post by Lukasz Tarkowski on 2011-07-22
yes it is shown, but I think I reached the limit.

---

### Post by Quackers on 2011-07-22
The 4 primary partition limit?
There are 4 partitions on there?

I think you really need to start at the beginning please.

---

### Post by Lukasz Tarkowski on 2011-07-22
Yes I have 4 primary partitions on my laptop NTFS partitions

---

### Post by Lukasz Tarkowski on 2011-07-22
I have to go to work now,  darn wish didn't have to delete extra partition :(

---

### Post by Quackers on 2011-07-22
I think that was worth mentioning in post 1.
I hope you haven't tried to create a 5th partition on that drive or Windows may have changed its partitions to dynamic disks. That's bad.
If you want to create more partitions on the disc you will need to delete a primary partition and replace it with an extended partition, in which there can be many logical partitions.
First though, I would check in Windows Disk Management screen to see if your NTFS partitions are reported as dynamic disks or simple volumes.

---

### Post by Lukasz Tarkowski on 2011-07-22
Now the problem is Ubuntu doesn't see Windows 7 64 bit SP1 HomePremium I am using Asus N50VN 500 GB 7200 RPM
still doesn't recognize my disk

---

### Post by Lukasz Tarkowski on 2011-07-22
I have no luck, I been googling and couldn't find the solution, I have a Baracuda Hdd.  Ubuntu won't recognize my Hdd, Its Half Hybrid and Part SSD

---

