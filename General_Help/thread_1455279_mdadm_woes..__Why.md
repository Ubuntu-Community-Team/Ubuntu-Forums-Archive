---
title: "mdadm woes..  Why?"
date: 2010-04-15
forum: General Help
---

### Post by scottac on 2010-04-15
About a week ago I decided to give another shot at trying to figure out how to use mdadm for a RAID 5 array. I was successful in creating the array however it seems as if the array wasn't assembling when I reboot. 

I will spare you all the details of what all I have done over the last few days to try and figure my problem out because in all honesty, I can't remember everything. But here is where I am at now. 

I have three 1TB drives I am trying to put into a RAID 5 array. I originally created the array a week ago and couldn't figure it out and honestly I was probably making things worse. So I decided to start from the beginning and wipe the drive of all data by running the following command.

```
dd if=/dev/zero of=/dev/hda bs=1M

```

Then using Gparted I created 3 1TB unformatted partitions and then set Raid Auto-Detect on all three drives. Then I used the following command to build the array

```
mdadm -v --create /dev/md0 --force --chunk=32 --level=raid5     --spare-devices=0 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

```

The array was created and started succussfully. So I then created a file system on the array with the following command

```
mkfs.xfs -b size=4096 -L mythtv /dev/md0 -f

```

Again this command completed without error. 

I added the following line to /etc/fstab

```
/dev/md0  /mount  xfs  defaults  0  0

```

and then ran the following command in the terminal

```
mount -a

```

I checked in /mount and sure enough the drive had been mounted as evidenced by the 2TB of available space

Keep in mind that I never set up a /etc/mdadm.conf file. The reason I didn't is because a week ago when I had originally tried to get this array fucntional I did create a mdadm.conf file and my array wasn't being assembled on boot anyway. I have a feeling however, that  this mdadm.conf file is the source of my issues.

Anyway. I then rebooted after I mounted the drive and sure enough, just like a week ago, the drive wasn't mounted.

I ran the following command to see if my array would mount

```
sudo mount -a
mount: special device /dev/md0 does not exist

```

I used the following tutorial when building my array

[http://www.mythtv.org/wiki/RAID](http://www.mythtv.org/wiki/RAID)

and I originally did set up a mdadm.conf file as instructed on this page.

I am coming here for help. I really have now idea how to build this file. 

Someone please help. I have no idea where to go from here.

---

