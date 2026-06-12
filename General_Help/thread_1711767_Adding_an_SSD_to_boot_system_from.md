---
title: "Adding an SSD to boot system from"
date: 2011-03-21
forum: General Help
---

### Post by Frogster on 2011-03-21
Good evening,
I have a very simple question, I am thinking of adding an Intel 80GB X25-Mainstream SSD to boot from. 

1. If I change the boot order in the Bios so that the SSDis the primary boot drive can I just install to the ssd and will that leave all data on the other drives?

2. I currently have two hard drives one has / and /home on it. The ssd will be added and ubuntu installed prior to reformatting the drive with / and /home. Will this cause problems?

Any advise will be greatly appreciated

---

### Post by oldfred on 2011-03-21
You should not have any problems, but backups are still advised. We have users (including me) who have clicked on format the wrong partition/drive and lost data.

If you install to the SSD first you can copy some or all of your /home settings over if you want. I only copy some from each new install. I do keep a working copy of Ubuntu on every drive in my 20-25GB / partition and keep all data in /data or /shared (NTFS) that I mount in every install.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by Frogster on 2011-03-21
Thank you oldfred,

All photos, docs and mp3s are on the 3rd drive and I think I will remove that one prior to the install. All passwords are synced so I think all is covered.

Thanks for the links

Now to buy the drive :D

---

