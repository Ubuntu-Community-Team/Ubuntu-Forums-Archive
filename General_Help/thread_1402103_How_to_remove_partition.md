---
title: "How to remove partition?"
date: 2010-02-08
forum: General Help
---

### Post by AquaFusion on 2010-02-08
How do I remove a partition through 9.04? I already have Gparted installed through apt-get. Removing is not a problem, the problem is how the heck do I know which partition I am using? I prevously installed 9.10 before and it went back, so i reinstalled 8.10 through my Linux Guru? friend help (see the question mark? you see why i mean by that). then I, myself,  upgraded it to 9.04. When I was reinstalling 8.10, I see two partition on my hard drive, first is NTFS (window xp) and the ext4 partition (but the Live CD see it as ext3 partition). I attempted to delete the ext4 partition, it just did nothing which make me think it did something. So I refreshed the screen and found out the ext4 is still there. So I ask my Linux Guru friend to help out. He went through custom setting to remove partition and he think he did it. and display a Welcome screen to set up my account. But my guts telling me that he didn't remove the ext4 partition. While he looking away, i went back to the partitioner screen and found out it still there. So i was like screw it and went ahead to create a new partition for 8.10 (but it shorten my Window partition which i need that for important things.) After installation, everything went ok. So i went back to my place and "sudo apt-get gparted" to bring up the GUI Parted. that where strange thing puzzled me. the Ubuntu 8.10 i am using show 50 GB filesystem, but Gparted show 60 and 70 GB ext 3 partition. I was confused how Gparted think i have more GB than what i set for. So I went to the root directory of my 8.10 then right click>proprieties to get the GB info. Then it displayed that I have around 65GB filesystem. I was puzzled why it showing that. So i thought possible if i mount the ext4 partition and able to get the right info. But as usual, it can't mount the ext4 partition as error said but my Gparted show they both a ext3 Partition, not one of them displayed ext4. Both of them are ext3. So I remember that I give my ext4 partition more GB than my 8.10 and found one partition. But when I checked the 70GB partition properties. It said it is mounted but the 60GB one is not mounted. I was puzzled why my ext4 is mounted but my ext3 is not mounted. Again I am not using LiveCD this time. I am using my 8.10 partition and on the desktop with Gparted open. So I just decided to gamble it and tell gparted to remove the "ext3" 70GB. But error show up and said something that it cant be removed because it is mounted.

I was sitting there and wondering "how the heck did my 8.10 is using my ext4 filesystem if it can't mount it on the desktop but it can mount fine through Gparted?" I am trying to understand what is happening. The reason why i want to remove the ext4 partition, so i can give back that partition to my NTFS partition, giving back the space that my window need for my important things.

Now I remember why it couldn't remove the partition. I thought it was a mount issue but I remember something. The ext4 partition is under Sda4 and sda5 while my current partition is using sda6 and sda7. So when i attempt to remove Sda4 and sda5, it said it can't remove because of the level of sda.

---

### Post by zvacet on 2010-02-09
> When I was reinstalling 8.10, I see two partition on my hard drive, first is NTFS (window xp) and the ext4 partition

It will be easier and you will not ask this question if you just deleted ext4 partition and on that free space installed Ubuntu.But that is past.If you have any valuable data back up them and make fresh install.This time you can download Jaunty and install it to avoid upgrading from Intrepid.Good idea is to make separate home partition during install so in case of reinstalling,fresh installing.... your settings and files/data will be safe on separate partition.

---

