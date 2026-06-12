---
title: "Strange partition table"
date: 2006-04-20
forum: General Help
---

### Post by StefanoCole on 2006-04-20
Hello, on my HD I had two partitions, one for Win XP and another for Ubuntu. A few days ago I decided to remove Win XP. So, with GParted I reformatted the Win partition into ext3. Now, if from Ubuntu I mount that partition it is shown as an ext3 partition and I can use it without any problems. What is strange to me is that if I do a: sudo fdisk -l /dev/hda

the partition is still reported as a NTFS partition.

Since I have no problems using that partition with Ubuntu I don't worry about it but, in any case my question is: why doesn't the partition table reflect the change?

Thanks in advance for any info

Stefano

---

### Post by oberoc on 2006-04-20
It's just a guess, but I think that even though you have reformatted the partition as ext3, you have changed the label and that it why it is come up at an NTFS partition. To change it, you would go into fdisk, pick the partition, and then cange the a partition's system id (choice t). 

HTH,
Tino

---

### Post by StefanoCole on 2006-04-20
Tino, thank you for the answer, I will try what you have suggested.

Stefano

---

