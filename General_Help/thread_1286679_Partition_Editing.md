---
title: "Partition Editing ??"
date: 2009-10-09
forum: General Help
---

### Post by NawafLol on 2009-10-09
Hey follow ubuntu users !

i have a duel boot :

1 - Ubuntu 9.04 225.6 GB 
2- windows vista 50.4 GB

and i don't have a home partition by it self !

Will i want to expand my windows partition to 60.4 gb ,without no date lost 

Is that possible ?

or i will be losing some important date  ?

P.S: Sorry for my english is not my first language !
 
I already have Gnome Partition Manger :)

---

### Post by pmlxuser on 2009-10-09
this does spell disaster if you try it.. well don't say we warned you.. having data in root partition is  bad practice. you might losose data but you can also loose the who system. goog luck

---

### Post by mechro on 2009-10-09
Decrease the Ubuntu partition size from Ubuntu LiveCD using Gparted.

Increase the Windows partition size from Windows using Windows?

You could increase the Windows partition size from Ubuntu but my suggestion is to try and keep problems to a minimum.

Don't forget to back up all your data before doing any partition manipulation.

---

### Post by ArcaVex on 2009-10-09
Try and grab a copy of Acronis Partition Expert, might even be a version on Hiren's Boot CD,

resize your ext3 partition by -10gb then resize ntfs by +10gb. 

backup before you resize in case.

---

### Post by NawafLol on 2009-10-09
ok that scared me XD !

so i got alot of Responds now i'm just confused !

so i think i will try the Live Cd and hope for the best !

(Damn me and my Noobish ways :P)

---

### Post by lovinglinux on 2009-10-09
I just did something similar, but I didn't messed with my Windows partition. Actually I have resized and moved all partitions in one of my drives. Everything went well. 

I had this:

/dev/sdb1 swap 1.9 GiB
/dev/sdb2 ext4 / 8 GiB
/dev/sdb3 ext4 /home 4 GiB
/dev/sdb4 ext4 /home/data 135 GiB

I wanted more space for sdb2 and sdb3, so I shrank and moved sdb4 to the right, leaving 10 GiB of unallocated space on the left. Then I moved sdb3 to the right and grew it to 8 GiB, then grew sdb2 to 12 GiB.

Keep in mind that moving a partition to the left is a much more complex operation. It takes a lot of time. For instance, my 135 GiB partition took 35 minutes to be shrank and moved to the right, while it took 2 hours to grow using unallocated space from the partition before it. So expect to wait some time to change your Windows partition size. Make sure you have an UPS in place, because if the power supply goes off during this operation you are probably screwed.

I don't know if you should perform Windows partition manipulations with a Windows tool. Gparted works pretty well, at least when manipulating my ext4 partitions. If you need an Windows tool, I would recommend PatitionMagic. I used it several times, including one time that I was unable to install Ubuntu on a notebook, until I created the ext3 partitions for Ubuntu from Windows using PartitionMagic.

Keep in mind that partition manipulation errors could screw your system. So backups are strongly advised. I never had an issue with moving, shrinking or growing partitions, but it's a risky operation, specially if you don't know exactly how to do it.

I also recommend that you plan ahead and better distribute the partition space. Creating a home partition is strongly advised. You can learn more about this [here](http://www.psychocats.net/ubuntu/separatehome).

Perhaps these will also help you:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

