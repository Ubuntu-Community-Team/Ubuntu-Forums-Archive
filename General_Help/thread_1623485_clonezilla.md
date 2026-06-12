---
title: "clonezilla"
date: 2010-11-16
forum: General Help
---

### Post by adwhitenc on 2010-11-16
I want to try to backup my system with [clonezilla]("http://clonezilla.org/"). I have available space on an external hard drive. However, I need to know if I will be able to clone my entire system(programs, settings, and home files), and be able to reinstall it in partitions.

Thank you in advance for your help.

---

### Post by emoguitarist06 on 2010-11-16
Yes you may, Clonezilla makes an exact copy of your hard drive including the partitions

I cloned my 80gb SSD that had "/ /home & swap" partitions to a 250gb hdd and when I booted Ubuntu only noticed the total 80gb that the partitions were setup as but using a live cd and gparted i just extended my /home partition

---

### Post by lmarmisa on 2010-11-16
If you wish to backup your system, I think that you could select the disk/partition image option and not the disk/partition cloning option.

---

### Post by adwhitenc on 2010-11-17
Cool, however, i will need to install my home (130gb) partition in a smaller partition (80-90gb) could I do this?

---

### Post by lmarmisa on 2010-11-17
This is one of the limitations of [clonezilla]("http://www.clonezilla.org/"):

[LIST]
[*]*The destination partition must be equal or larger than the source one*
[/LIST]
Therefore clonezilla does not solve your problem directly. But you could use Gparted as a auxiliary tool in order to shrink your target partition.

If your target physical disk is bigger than 130 Gbytes, you could restore the 130 Gbytes partition and then shrink it to 90 Gbytes using Gparted. Then continue with the restoration of the second partition and so on. You could use Gparted also in this process for defining each partition before its restoration.

This solution would require that clonezilla would save/restore or clone each partition individually (not using the full disk backup/restore/clone option).

---

### Post by adwhitenc on 2010-11-18
The thing is, I have to make a in the first spot to put Windows7. How on earth could I do that?

---

### Post by Mark Phelps on 2010-11-18
> **adwhitenc said:**
> The thing is, I have to make a in the first spot to put Windows7. How on earth could I do that?

I'm not an EXPERT with Clonezilla, but from what I've seen, it saves off the partition sequence as part of the image, that is, if the partition is "sda1" on the source drive, it saves it off as "sda1" also.  Thus, when you go to restore it to the target drive, if you already have an "sda1" there, my guess is that it would overwrite it.

If that's true, you would do the following:
1) Restore the old partition to the new drive
2) Use GParted to shrink the partition and move it to the right
3) Install Win7 to the unallocated space to the left of the partition.

Perhaps others, who are more expert in Clonezilla, have other suggestions?

---

### Post by lmarmisa on 2010-11-18
If you need help, maybe you could explain with more details what you want to do.

I am not sure but it seems that you wish to add a Windows 7 operating system to your computer maintaining your current operating system(s) (Ubuntu and perhaps others). I guest you do not intend to replace your current internal hard drive or add a new one. You plan to maintain your internal hard drive. Finally, you have an external USB hard drive that you plan to use for the backup of your current system.

Please, confirm if the previous assumptions are true.

I would like to see the output of this command too:

```

sudo fdisk -l

```

---

### Post by adwhitenc on 2010-11-30
I ended up just using tar to migrate everything onto an external hard drive. It was slow as crap though. Successful 7 install and Ubuntu 10.4 reinstall. Thanks for the help.

---

