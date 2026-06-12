---
title: "New installation on 2 disks"
date: 2009-10-20
forum: General Help
---

### Post by DeMus on 2009-10-20
Hi, my computer has a Asus P5K motherboard. Attached are 2 500GB harddisks.
I want to do a complete new install the moment Karmic is out. At the moment I have Windows taking the SDA disk and Jaunty the SDB disk.
Since I don't use Windows anymore I want to use both disks for Karmic.

What is the best way of doing that? I have an external disk to store all my data, so I can erase both disks completely.

Is LVM an option? Making a, let's say 50GB, partition for / and the rest of SDA plus the complete SDB for /home? If so, can someone describe in simple terms how to do that.

Is raid an option? I know the P5K does not support raid for the two internal SD disks, but maybe with a software solution which I read about it could be possible. I am thinking about raid 0. Yes I know there is no safety in raid 0, I just like to have the capacity of both disks added to get 1TB. In my former computer I had that also and never had problems with it.
How do I install Ubuntu on a raid 0 (when possible)?

Can I split my /home partition (folder?) on to 2 disks? If so how to do that?

Please, when giving me help do it in simple terms, cause for 1: English is not my native language and 2 I am still fairly new to Linux.

Thanks for all the help I will get. 8)

---

### Post by DeMus on 2009-10-21
Maybe you guys (and girls) didn't understand the last line of my first post:
Thanks for all the help I will get. 8)

It means I am waiting for your help. So come on, don't let me down.

---

### Post by iBurger on 2009-10-21
Since Linux Software raid works on 'partition level' rather than 'drive level' you can have a combination of raid0 (striping) and raid1 (mirroring).

If you have two equal hard drives, named, sda and sdb, you could setup your raid up like this:

raid1: sda1 (40gb)  + sdb1 (40gb) = /dev/md0 (40gb)            
raid0: sda1 (460gb) + sdb2 (460gb) = /dev/md1 (920gb) 

The linux system would be installed on raid1 device (/dev/md0), which is really secure. Please note, that an actual raid setup is a bit more complicated because you need a separate /boot/ partition for GRUB. 

Also see this page;
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-raid-diskdruid-manual-devmnt.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-raid-diskdruid-manual-devmnt.html)

---

### Post by DeMus on 2009-10-21
> **iBurger said:**
> Since Linux Software raid works on 'partition level' rather than 'drive level' you can have a combination of raid0 (striping) and raid1 (mirroring).

If you have two equal hard drives, named, sda and sdb, you could setup your raid up like this:

raid1: sda1 (40gb)  + sdb1 (40gb) = /dev/md0 (40gb)            
raid0: sda1 (460gb) + sdb2 (460gb) = /dev/md1 (920gb) 

The linux system would be installed on raid1 device (/dev/md0), which is really secure. Please note, that an actual raid setup is a bit more complicated because you need a separate /boot/ partition for GRUB. 

Also see this page;
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-raid-diskdruid-manual-devmnt.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-raid-diskdruid-manual-devmnt.html)

Thank you for your answer.
In the mean time I have been reading a lot and I think I want something like this.
Since I want to have a raid 0 (for speed rather than a raid 1 for safety) I think I partition the discs as follows:

[FONT="Courier New"]sda1: 100MB /boot..........sdb1: 100MB dummy
sdb2: 50GB  /...............sdb2: 50GB  /.............raid 0
sdb3: 450GB /home..........sdb3: 450GB /home........raid 0[/FONT]

I read also I need a separate partition for /boot, so that will be sda1. Partitions 2 and 3 on both disks will be put into the raid 0.
Partition sdb1 is a dummy partition to make sure both disks are exactly the same.

Is there anything against this way of doing it? Will I get problems this way (apart from losing everything when a disk should crash), will this work eventhough my motherboard (Asus P5K) has no Raid capabilities for the internal serial disks?

---

### Post by NightwishFan on 2009-10-21
I have found an Ubuntu resource on RAIDs.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by Slim Odds on 2009-10-21
> **DeMus said:**
> Since I want to have a raid 0 (for speed rather than a raid 1 for safety) I think I partition the discs as follows:

[FONT=Courier New]sda1: 100MB /boot..........sdb1: 100MB dummy
sdb2: 50GB  /...............sdb2: 50GB  /.............raid 0
sdb3: 450GB /home..........sdb3: 450GB /home........raid 0[/FONT]

I read also I need a separate partition for /boot, so that will be sda1. Partitions 2 and 3 on both disks will be put into the raid 0.
Partition sdb1 is a dummy partition to make sure both disks are exactly the same.

Is there anything against this way of doing it? Will I get problems this way (apart from losing everything when a disk should crash), will this work eventhough my motherboard (Asus P5K) has no Raid capabilities for the internal serial disks?

You're on the right track. I use a very similar setup with 8.10. The main difference is that I that I have more partitions (for /var /tmp etc.)

The main issue in setting up the software RAID is that you have to manually load mdadm if you're using the LiveCD. Otherwise you can use the alternate install CD.

I'm not sure if that has changed since 8.10, but I like the setup a lot. Very fast.

---

### Post by DeMus on 2009-10-21
> **NightwishFan said:**
> I have found an Ubuntu resource on RAIDs.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Thanks, I did read that page already, but wasn't quite sure about it. Now I know I'm on the right track.
Thanks again.

---

### Post by DeMus on 2009-10-21
> **Slim Odds said:**
> You're on the right track. I use a very similar setup with 8.10. The main difference is that I that I have more partitions (for /var /tmp etc.)

The main issue in setting up the software RAID is that you have to manually load mdadm if you're using the LiveCD. Otherwise you can use the alternate install CD.

I'm not sure if that has changed since 8.10, but I like the setup a lot. Very fast.

At the moment I also have extra partitions for /var and /usr, but are they really necessary? I mean I can make them again, but does it make sense to do so?

---

### Post by NightwishFan on 2009-10-21
I gave you absolutely no help, but I was happy to try. :popcorn: Please tell me how it all works out, and good luck.

As for the /var and /usr, I would have to say it is not strictly necessary, but it can provide certain benefits. The main one I can think of is to prevent certain parts of the filesystem from getting too large on their own.

---

### Post by Slim Odds on 2009-10-21
> **DeMus said:**
> At the moment I also have extra partitions for /var and /usr, but are they really necessary? I mean I can make them again, but does it make sense to do so?

No, you don't really need them. Just keeping a separate /home is fine.

---

