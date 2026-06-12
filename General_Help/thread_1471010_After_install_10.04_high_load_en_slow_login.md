---
title: "After install 10.04 high load en slow login"
date: 2010-05-03
forum: General Help
---

### Post by Lostsouls on 2010-05-03
So I just reinstalled Ubuntu 10.04 LTS and now I'm facing some troubles,

1st of al, it takes a very long time after to login for my desktop to load ( about 15 - 20 sec ). A college of mine said it may be related to some HD drives being mounted ( i have 2 disk and multiple partitions of ext4 and ntfs )

2nd My average load is way higher then on 9.10, i justed to idle along 0.2 - 1.5 at max maiby when run virtual box with xp and a lot of open windows. But now even when my pc is doing nothing ( cpu load of 5 - 10 % ) it stays above 0.2 and it frequently jumpes to 1.5 -2.5.

3rd, and this is somthing i have an issue with a long time, when I minimize windows to the taskbar and maximizes them again it takes about 0.5 - 2 seconds before there on the screen again. I dont quite get that because If I run Ubunut in a virtual box on the same machine it maximizes windows faster then the host system :S

So i really would appreciate it if someone could help me :)

Some machine specs,

Ubuntu 10.04 32 bit
Athlon X2 5200+ @3.0Ghz
4gig ddr2 RAM @900mhz
Asus 4870 512MB Stock

Disks,

1 WD 500 gig @7200rpm sata2
--- 4 partitions
1 windows boot 100mb NTFS
1 windows os 7 370gb NTFS
1 linux 10.04 100gig EXT4
1 swap           4gig   EXT4

1 Samsung eco green 1.5 TB @5400
--- 1 partition
1 Data 1.5 TB NTFS

Video card was installed with auto driver search from ubuntu :D

I'd appreciate any help, just ask me which logs you need,

EDIT: there is a 4th issue, firefox is slow as hell ( not loading pages but switching tabs, opening tabs ), only thing I hav extra on it atm is a persona theme, but no other plugins only the ubuntu plugin :S

---

### Post by periphery on 2010-05-06
I have the same problem with just one harddrive upon logging in the system runs with extremely high load (between 4 - 6) for about ten minutes. All applications run super slow and the system is barely usable.

---

### Post by Tamale on 2010-05-11
We need to treat this as a major issue.  You two aren't the only ones experiencing this problem after upgrading to 10.04:

[http://ubuntuforums.org/showthread.php?t=1476093&highlight=higher+load+average](http://ubuntuforums.org/showthread.php?t=1476093&highlight=higher+load+average)

My server used to average between 0.01 and 0.05 under normal usage, but now rarely drops below 0.2... almost a 10x increase in average load. Something is screwy, and it's not compiz.. I've switched back to metacity (which helped, but only barely).

---

### Post by otchie1 on 2010-05-16
Well I get the slow to appear desktop but with no appreciable load at all (0.21)

I run 4GB 800 DRAM with Phenom II 965.

3 separate hdd.

Can't believe it's disk mount related as if i leave the box at login and instead ssh into it everything is there already.

It's just the wallpaper and icons that are slow...taskbars are there from the off.

---

### Post by 81084997 on 2010-05-16
> **otchie1 said:**
> Well I get the slow to appear desktop but with no appreciable load at all (0.21)

I run 4GB 800 DRAM with Phenom II 965.

3 separate hdd.

Can't believe it's disk mount related as if i leave the box at login and instead ssh into it everything is there already.

It's just the wallpaper and icons that are slow...taskbars are there from the off.

Ubuntu devs believe you need floppy and ipv6 modules loaded.
Bet you haven't got a floppy drive or an ipv6 router?

blacklist them in /etc/blacklist.conf
and then amend the initrmfs with

```
sudo update-initramfs -u
```

---

### Post by alejandro.mc on 2010-05-23
I have the exact same problem, really need a hand, the 20 seconds desktop loading is killing me..

Thanks·.

SOLVED FOR ME: Disabled the Floppy from BIOS (I have no floppy drive and apparently that created a conflict..strange..)

---

### Post by randyklein99 on 2010-06-04
> **alejandro.mc said:**
> I have the exact same problem, really need a hand, the 20 seconds desktop loading is killing me..

Thanks·.

SOLVED FOR ME: Disabled the Floppy from BIOS (I have no floppy drive and apparently that created a conflict..strange..)

Just wanted to say that disabling floppy from bios had the same affect for me.  Took a slow login to Desktop (20secs or so) to about 2-3 secs.

---

### Post by sayantandas on 2010-06-10
I have no floppy drive on my laptop. why do I have slow load times? It must be something else! ipv6 is already disabled on my system.

---

### Post by yyx on 2010-06-14
I'm also using a laptop with no floppy drive, so there is nothing to disable in the bios.  I followed [these steps]("http://ubuntuforums.org/showthread.php?t=591420") to disable the floppy drive:
> Open up a terminal and type sudo gedit /etc/fstab. Enter your password. Comment out (i.e., put a number sign -- # -- next to) the floppy drive line. Save it and exit.

After this change the time from login to desktop shortened from ~20s to under 4s.  Hope this helps.

---

### Post by sayantandas on 2010-06-16
I do not have anything in /etc/fstab which says floppy on  my laptop.

Here is my fstab.

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8eb9f992-4663-4762-a020-e3f39704815e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=1ea46884-b10a-425d-af36-290e3e47baf9 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=64ed61f0-fd5a-48a0-9aa3-7a0b742a8c86 none            swap    sw              0       0
~                                                                                                                                                                                                                                            
~                                                                                                        


So what to do now????

---

### Post by Arkish0 on 2010-08-03
same for me! no floppy line =(.. any ideas!


thanks!


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=275f784c-e1bc-44f1-ba8f-c8355735d9e4 /               ext4    errors=remount-ro 0       0
# swap was on /dev/sda6 during installation
UUID=95414c6b-6ea1-4137-9cca-daba8527307d none            swap    sw              0       0

---

### Post by Manu_b on 2010-09-17
Hi,

I had pretty the same thing with 10.04 server edition, till I found that the raid5 array was beeing resync'ed 

The Avg load was ~1.5 with very low cpu usage, that made me think of I/O problem.

Of course this is a fresh install, that's why the array was synchronizing after the install.

sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Thu Sep 16 22:52:14 2010
     Raid Level : raid5
     Array Size : 585937728 (558.79 GiB 600.00 GB)
  Used Dev Size : 195312576 (186.26 GiB 200.00 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Sep 17 21:33:41 2010
          State : active, resyncing
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 85% complete

           UUID : b540434f:8d8b3d2e:087e2241:cdc009e6
         Events : 0.49

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2

any of you are using software raid ?

regards,
Manu

---

