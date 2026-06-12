---
title: "Lenovo OneKey Recovery changed a partition"
date: 2011-09-09
forum: General Help
---

### Post by Bjor on 2011-09-09
What happend?

I have a dual boot, Ubuntu, Windows machine, both on a seperate partition and i have a 3th data partition
In windows i wanted to make a recovery cd with a program called Lenovo Onkey Recovery. This didn't work because i made changes on the partition and this little program coulden't handle them. No worries, i'll get my recovery cd in another way.

But,
In the process this little program edited my NTFS data partition, to "Compaq Diagnostic (0x12)" file system, so its hidden for windows and doesn't mount automatically in Ubuntu.
my data is still on it.

So, my question:
how can i change the file system on my data partition back from "Compaq Diagnostic (0x12)" to "HPFS/NTFS (0x07)" without erasing all my data?

I did try System>Administrator>Disk Utiliy but this gave a time-out error
In Gparted the data partition is considered as a normal NTFS partition, so Gparted can't help me neither...

Thanks for advise

---

### Post by Habitual on 2011-09-09
I believe ranish can change the partition type.

[http://www.ranish.com/part/](http://www.ranish.com/part/)

---

