---
title: "LVM mysteries in Ubuntu"
date: 2011-07-02
forum: General Help
---

### Post by SOMDdan on 2011-07-02
Hi, I need some help answering some questions about LVM:

Recently I had a hard drive failure, and had to reload my system from scratch.  I decided to use LVM (for the first time) when I reloaded Lucid. I used the alternate install CD to install 10.04 with LVM, using the defaults. It works fine, and since then I have done enough research on LVM to understand the structure overall. My installation is like this: A single 250Gb HD with a small boot partition and the rest of the disk is an extended partition with a 250GB LVM2 Physical Volume. 

Here are the results of ***pvdisplay, vgdisplay ***and*** lvdisplay***

[I][B]pvdisplay 

  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               ubuntu
  PV Size               232.65 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              59557
  Free PE               1
  Allocated PE          59556
  PV UUID               XUUca1-z20Y-HFzv-KCtI-19jS-wABB-UzjJin

[/B][/I][I][B]
  --- Volume group ---
  VG Name               ubuntu
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               232.64 GiB
  PE Size               4.00 MiB
  Total PE              59557
  Alloc PE / Size       59556 / 232.64 GiB
  Free  PE / Size       1 / 4.00 MiB
  VG UUID               MgLLec-l7wY-4V97-dWi1-sGy8-xH76-2QnRJ1[/B][/I]
[I][B]

lvdisplay

  --- Logical volume ---
  LV Name                /dev/ubuntu/root
  VG Name                ubuntu
  LV UUID                0Ky33V-MCNh-AeVY-Oa3U-rDzd-WT6x-WVtyZk
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                224.02 GiB
  Current LE             57349
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/ubuntu/swap_1
  VG Name                ubuntu
  LV UUID                OuBkDW-xVRw-RSel-zQZz-GO8D-fp3O-3Pj5Va
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                8.62 GiB
  Current LE             2207
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1








[/B][/I]I could just leave it the way it is and not think anymore about it, **BUT **the hard drive failure made me get very serious about backing up things and properly partitioning the hard drive.

In the old scheme, I would have set up a separate home partition during installation that was easy to backup by pointing a backup program at my home directory's /dev name, but LVM has so many more components that such a process becomes much more murky. Part of the problem is that during installation I did not know what I now  know about LVM and I blindly accepted the defaults for setting up LVM, and as a consequence, I now have a single large LV that holds *everything.* I really want to have my /home directory on a separate LV that can be backed up by itself, like I was able to do before installing LVM. Under the old way, I would handle partition management by booting into my VERY handy Linux System Rescue CD and use the partitioning tool to resize or create/delete partitions. 

So given that here are the questions I am having a hard time answering:

1) How can I break a new LV off of the /dev/ubuntu/root LV just for my /home data?

2) How do you make external backups of the data that is organized by Logical Volumes?

3) Do the standard rescue CD partitioning tools apply to working with LVM partitions/volume groups/logical volumes?

Thanks for helping with these questions.

---

### Post by bodhi.zazen on 2011-07-02
You can move your home, you would need to downsize your LVM.

[http://tldp.org/HOWTO/LVM-HOWTO/reducelv.html](http://tldp.org/HOWTO/LVM-HOWTO/reducelv.html)

[http://fedorasolved.org/Members/zcat/shrink-lvm-for-new-partition](http://fedorasolved.org/Members/zcat/shrink-lvm-for-new-partition)

[http://fedorasolved.org/Members/zcat/a-new-home/a-new-home](http://fedorasolved.org/Members/zcat/a-new-home/a-new-home)

You can also use LVM snapshots

[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

---

### Post by SOMDdan on 2011-07-04
Thanks Bodhi, that did the trick!\\:D/

---

### Post by Seq on 2011-07-04
For future reference, generally you would have your logical volumes sized for how much data they require, rather than to fill the volume group. Leaving some free space gives you room to change how you're using the disk.

For example, I have (on my work machine) a 75GB volume group, but I've only assigned 55GB of that to logical volumes, with 20GB unallocated. This gives two benefits:
[LIST]
[*]Should I need a new filesystem for some application, I can create it with the free space
[*]I can backup a snapshot instead of a live filesystem. Snapshots use unallocated space as an overlay so the original filesystem can still write
[*]Should I need to resize a partition, I can just add 5GB and be done with it.
[/LIST]

The thing to remember is that you can create, destroy, and grow logical volumes on a live system. But to shrink, you must umount it (this is problematic if the filesystem you want to shrink is an important one, like /)

---

