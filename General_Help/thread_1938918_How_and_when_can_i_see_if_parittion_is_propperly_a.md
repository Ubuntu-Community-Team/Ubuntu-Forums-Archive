---
title: "How and when can i see if parittion is propperly aligned in Kubuntu?"
date: 2012-03-10
forum: General Help
---

### Post by mastablasta on 2012-03-10
OK, so i got this WD Green 750 GB disk that was making porblems as system disk for WindowsXP and moved it into a linux maschine to see if i encounter any errors using it in Linux. However this disk is one fo those new disks where you need to align the partition in windowsXP to make them work propperly. 

I run Kubuntu 11.10 live, installed gparted to it and then reformat the disk into 1 partition which i intend to use for data. I used the default settigns which i read should align the partitions just fine.

my question is how can i see if the partition is propperly aligned in Kubuntu 10.10? i've checked it out with Dolphin, Kinfocenter, but none of them report any device not workign propperly or a missaligned partition.

---

### Post by Topsiho on 2012-03-10
I don't know whether I can answer your question, I don't know what is meant with "aligned". But in the past I had some problems with disks being partitioned in Partition Magic, in Windows, and disks being partitioned with GParted. The difference was, as I understand, where the partition boundaries are: at the cylinder boundaries ("aligned"?) or not.

Partition Magic is long history now, so I have not met this problem for a long long time. I am sorry I don't know how you can check the partition boundaries, maybe you should calculate and check them in the partition table.

Topsiho

---

### Post by winh8r on 2012-03-10
You might find this helpful:

[http://tinyurl.com/yzkph26]("http://tinyurl.com/yzkph26")


Hope so.

---

### Post by mastablasta on 2012-03-11
this is what i am talking about - advanced file format: [http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system]("http://wdc.custhelp.com/app/answers/detail/a_id/5655/%7E/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system")

now it seems like gparted form 11.10 correctly aligned them. my quesiton is how do i verify that in Kubuntu?

In ubuntu i think disk utility pops out an error saying the disk is missaligned.
Like this for example: [http://i.stack.imgur.com/gyIm5.png](http://i.stack.imgur.com/gyIm5.png)
---
Ok so i did some search this time instead for solution i searched for a problem and it seems this command should say if it is aligned to 4kb sectors: 

sudo fdisk -lu /dev/sdb

not a gui but i guess it will do. 

more on this topic here: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

