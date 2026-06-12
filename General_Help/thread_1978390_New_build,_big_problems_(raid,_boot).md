---
title: "New build, big problems (raid, boot)"
date: 2012-05-11
forum: General Help
---

### Post by Johnius on 2012-05-11
Well, after 10 years, I decided to buy a new computer.  I wanted all the bells and whistles, so an AMD FX-8150 and a Gigabye UD3 board with three 1tb drives found themselves in my possession. So I grabbed my 12.04LTS ISO and set to work making a RAID 5 array.  Fakeraid is a no-go because Linux doesn't have drivers for my chip. So I used the alternate install to partion each of my three disks identically:  100mb for boot, 2gb for swap, 10gb for root, and the rest for home. It installed well enough and seemed to work... then it wouldn't boot after a power failure. I tried to rebuild the array (PITA, BTW). I got it working, just in time for Linux to forget about sdc. Well, all my drives show in the BIOS. I reboot with the live cd and set to work... three reboots later, sdc finally loads as a device and back to "sudo mdadm..."  The arrays report full functionality, but refuse to boot. Great. So I try to reinstall only to get an error when the kernel attempts to install. So I tried formatting the RAID disks, then deleted them, then made them again, then erased the partitions on the physical disks.  Now I'm returning them to RAW in hopes I can have a computer soon. Obviously I'm doing something wrong because linux RAID is supposed to be highly reliable and efficient and this is the second time I've had to use a secure erase on these disks. Thanks for listening... and if you're a programmer, thank for programming!

---

### Post by Johnius on 2012-05-12
And now the installer dies on "cannot install 'linux-generic'" and so I tried to update my version only to have my USB stick unbootable...

---

### Post by SeijiSensei on 2012-05-12
I avoid using RAID for /boot or /. I'll use it for /var and /home, and occasionally /usr, but I prefer to have the machine boot from an ordinary partition.  Also there's no reason to use RAID for swap.  You can create separate swap partitions on each drive and Linux will use them all without RAID.

On a machine like yours I'd partition as follows:

/dev/sda1 - 512 MB for /boot with ext2
/dev/sda2 - 2 GB swap; will be 6 GB overall with /dev/sdb2 and /dev/sdc2
/dev/sda3 - remainder as extended
... /dev/sda5 - 5 GB for / with ext4
... /dev/sda6 - 10 GB for /usr with RAID and ext4
... /dev/sda7 - 5 GB on desktops, 10-30 GB on servers, for /var with RAID and ext4
... /dev/sda8 - remainder for /home with RAID and ext4

/dev/sda6-8 can be RAIDed with equivalent partitions on /dev/sdb and /dev/sdc.

You can copy the contents of /dev/sda1 and /dev/sda5 to the equivalent partitions on the other drives.  Then edit /boot/grub/grub.conf on /dev/sdb1 and /dev/sdc1 to use the corresponding /dev/sdb5 and /dev/sdc5 as the root partition in each case.  After installing grub to the master boot record on each drive you can then boot from /dev/sdb or /dev/sdc if /dev/sda goes south.

---

### Post by Johnius on 2012-05-12
It won't even let me install the kernel. I don't understand, it worked last week and now it's broken?

---

### Post by SeijiSensei on 2012-05-12
Are you saying you can't boot from the CD?  It sounds like that worked for you before.  Or are you trying to install a new kernel on an existing installation?  Your original post is a bit long and hard to follow.  

Try booting from the CD and running Try Ubuntu when offered.  When it's finished booting, can you see the hard drives with either gparted or by running fdisk in a terminal (e.g., "fdisk /dev/sda")?  If so, try deleting all the existing partitions on all the drives and reconfiguring them.  

If I were you, I'd start by simply partitioning /dev/sda to have /boot, swap, and an extended partition, then creating a 10 GB logical partition for / as /dev/sda5.  Now try installing.  If that works, you can partition the rest of /dev/sda and the other disks and create the arrays manually using mdadm from the command prompt.

---

### Post by Johnius on 2012-05-12
I use the alternate install disks because they're easier.  But the images I had were (and still are) looking for packages that apparently don't exist anymore, so I end up with a giant red screen and "failed to install kernel" (on a freshly formatted partition).

---

### Post by Johnius on 2012-05-24
And for the second time, I get everything installed, running (even rebuilt the array once after mdadm forgot what partitions it was supposed to have), and it forgets the partition table on SDC.  No rhyme or reason.  The drive is installed and 
```
sudo mdadm --detail /dev/md3
[sudo] password for john: 
/dev/md3:
        Version : 1.2
  Creation Time : Sat May 12 11:04:26 2012
     Raid Level : raid5
     Array Size : 1929890816 (1840.49 GiB 1976.21 GB)
  Used Dev Size : 964945408 (920.24 GiB 988.10 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu May 24 15:33:53 2012
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : BlackMamba:3  (local to host BlackMamba)
           UUID : 6d578708:326ec7cc:f89049a3:24856ff6
         Events : 944

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       20        1      active sync   /dev/sdb4
       2       0        0        2      removed

```

I'm completely at a loss, the disk is still there, but Linux won't read the partition table (again).  I have no idea what the issue could be and my 'friends' have offered to BUY me Windows 7... which I'd be horribly embarassed to accept.

---

### Post by Johnius on 2012-06-06
This continues to happen, I just ran the same command.  Why is mdadm kicking my disk?

---

