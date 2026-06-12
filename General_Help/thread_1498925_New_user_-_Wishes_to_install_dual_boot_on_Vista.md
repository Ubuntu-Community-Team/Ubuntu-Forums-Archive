---
title: "New user - Wishes to install dual boot on Vista"
date: 2010-06-01
forum: General Help
---

### Post by chaznsc on 2010-06-01
Hello,
I'm interested in installing ubuntu at home and have never attempted this before. I would like to use the EASEUS Partition Manager to resize my Windows Vista partition. 

Am I going to toast the machine in using EASEUS? If I set up a new partition, does it need to be large enough to simply hold Ubuntu or do all the programs I install need to be installed on that partition? My understanding is I only need to make the ubuntu partition 15gb and I can use the Vista Partition for everything else. 

Thanks in advance

chaz

---

### Post by Roasted on 2010-06-01
I am not familiar with that partition manager. I trust GParted Partition Editor the most out of all of them that I've used. I just burn GParted to a CD, boot to it, and handle the partitioning process accordingly.

You can set up your partitions however you like. YES - you can give Ubuntu only 15gb and just use files off of your Vista partition. That will certainly work. On my systems, I do the opposite. I try to give Windows as little space as possible while still being reasonable since I use Windows to game. Everything else is done in Ubuntu.

My mother dual boots XP and Ubuntu and her setup is identical to what you want to do. She has no complaints.

---

### Post by philinux on 2010-06-01
> **chaznsc said:**
> Hello,
I'm interested in installing ubuntu at home and have never attempted this before. I would like to use the EASEUS Partition Manager to resize my Windows Vista partition. 

Am I going to toast the machine in using EASEUS? If I set up a new partition, does it need to be large enough to simply hold Ubuntu or do all the programs I install need to be installed on that partition? My understanding is I only need to make the ubuntu partition 15gb and I can use the Vista Partition for everything else. 

Thanks in advance

chaz

Cleanup, backup backup and backup. Chkdsk then defrag twice. Then use vista's in built partitioning tool to do the job.

Also have a good read too.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by jarviser on 2010-06-01
> **chaznsc said:**
> Hello,
I'm interested in installing ubuntu at home and have never attempted this before. I would like to use the EASEUS Partition Manager to resize my Windows Vista partition. 

Am I going to toast the machine in using EASEUS? If I set up a new partition, does it need to be large enough to simply hold Ubuntu or do all the programs I install need to be installed on that partition? My understanding is I only need to make the ubuntu partition 15gb and I can use the Vista Partition for everything else. 

Thanks in advance

chaz
Most Ubuntu installers give you options, one of which is to install Ubuntu "side by side" with windows, and it will decide how much to shrink the old C: partition. Make sure you defrag the Windows stuff first.
For someone new to Linux that may be the best way.

If you do want to use GParted to take more control, shrink the Windows partition first then add in the remaining space **three new **partitions
One at 1GB and mount it as "swap"
One at about 15GB or more and mount it as "/" format ext4
Finally one as big as possible (the remainder) and mount it as "/home" formatted ext3. This is where you can keep your docs, pictures music etc. 
You will need to make some or all of the new partitions extended partitions because Vista hogs one boot partition, and one for C:

 If as above suggestion you keep the main files on the Windows partitions, the /home can be just a few GB and you will need to make a change to the "fstab" file to have them mount every time.

I write some articles here that may help
[http://www.jarviser.co.uk/jarviser/ubuntulucidondell1520.html](http://www.jarviser.co.uk/jarviser/ubuntulucidondell1520.html)
[http://www.jarviser.co.uk/jarviser/mint8ondell1520.html](http://www.jarviser.co.uk/jarviser/mint8ondell1520.html)

---

### Post by philinux on 2010-06-01
I would use ext4 for the root partition and /home.

---

### Post by chaznsc on 2010-06-01
> **jarviser said:**
> Most Ubuntu installers give you options, one of which is to install Ubuntu "side by side" with windows, and it will decide how much to shrink the old C: partition. Make sure you defrag the Windows stuff first.
For someone new to Linux that may be the best way.

If you do want to use GParted to take more control, shrink the Windows partition first then add in the remaining space **three new **partitions
One at 1GB and mount it as "swap"
One at about 15GB or more and mount it as "/" format ext4
Finally one as big as possible (the remainder) and mount it as "/home" formatted ext3. This is where you can keep your docs, pictures music etc. 
You will need to make some or all of the new partitions extended partitions because Vista hogs one boot partition, and one for C:

 If as above suggestion you keep the main files on the Windows partitions, the /home can be just a few GB and you will need to make a change to the "fstab" file to have them mount every time.

I write some articles here that may help
[http://www.jarviser.co.uk/jarviser/ubuntulucidondell1520.html](http://www.jarviser.co.uk/jarviser/ubuntulucidondell1520.html)
[http://www.jarviser.co.uk/jarviser/mint8ondell1520.html](http://www.jarviser.co.uk/jarviser/mint8ondell1520.html)


So it is possible to simply install Ubuntu without worrying over the partition issues?

---

### Post by philinux on 2010-06-01
> **chaznsc said:**
> So it is possible to simply install Ubuntu without worrying over the partition issues?

We have had many users over the years installing ubuntu who have wiped their windows install. Make sure you read everything first and pay particular attention to the installer at the **partitioning phase**.

Thats why the emphasis on backup and also make sure you have your windows install disc handy if things go wrong.

---

### Post by chaznsc on 2010-06-01
Well, I certainly don't want to wipe my system out, Im just so tired of Windows I thought I might spin out a Ubuntu system to see how I like it. I consider my abilities above par, but admittedly I have never installed a dual boot or had any experience with Ubuntu / Linux.

---

