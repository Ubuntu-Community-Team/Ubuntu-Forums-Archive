---
title: "new raid /dev/md0 disappears after reboot!"
date: 2009-07-26
forum: General Help
---

### Post by Drunken on 2009-07-26
Hi, whenever I set up a new raid0, it works fine, until I reboot and try to mount it again. Here's what I did to set it up:

(note /dev/sdc is my main drive, sda and sdb are new SATA harddrives)
```

#fdisk /dev/sda
Command (m for help): n (create a new primary partition)
Command (m for help): t (then select da for "non-fs data")
Command (m for help): w (write changes to disk and quit)

#fdisk /dev/sdb
Command (m for help): n (create a new primary partition)
Command (m for help): t (then select da for "non-fs data")
Command (m for help): w (write changes to disk and quit)

``````

#mdadm --create --verbose /dev/md0 --level=stripe --raid-devices=2 /dev/sda1 /dev/sdb1
#mkfs.ext3 /dev/md0
#mkdir /raid1
#mount /dev/md0 /raid1

```And here all works successfully.
But when I restart, /dev/md0 is gone.
This is on a clean Ubuntu 9 x86 installation.


Also here is some information about the system before I do the restart:
```

root@ubuntu-raid:~# cat /proc/mdstat
Personalities : [raid0]
md0 : active raid0 sdb1[1] sda1[0]
      8385664 blocks 64k chunks

unused devices: <none>

``````

root@ubuntu-raid:~# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 26 Jul 2009 16:16:31 -0400
# by mkconf $Id$

``````

root@ubuntu-raid:~# mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Jul 26 16:18:35 2009
     Raid Level : raid0
     Array Size : 8385664 (8.00 GiB 8.59 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 26 16:18:35 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 6b402e82:fec208ab:c4e69391:c984b73c (local to host ubuntu-raid)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```...now I reboot the machine (#shutdown -r now).


During reboot, I see a message saying
```
Starting MD monitoring service mdadm --monitor               [ OK ] 
```which I believe is a good thing.
Now back at the shell I type:
```

root@ubuntu-raid:~# ls /dev/md* -l
brw-rw---- 1 root disk 254, 0 2009-07-26 16:26 /dev/md_d0
lrwxrwxrwx 1 root root      7 2009-07-26 16:26 /dev/md_d0p1 -> md/d0p1
lrwxrwxrwx 1 root root      7 2009-07-26 16:26 /dev/md_d0p2 -> md/d0p2
lrwxrwxrwx 1 root root      7 2009-07-26 16:26 /dev/md_d0p3 -> md/d0p3
lrwxrwxrwx 1 root root      7 2009-07-26 16:26 /dev/md_d0p4 -> md/d0p4

/dev/md:
total 0
brw------- 1 root root 254, 0 2009-07-26 16:26 d0
brw------- 1 root root 254, 1 2009-07-26 16:26 d0p1
brw------- 1 root root 254, 2 2009-07-26 16:26 d0p2
brw------- 1 root root 254, 3 2009-07-26 16:26 d0p3
brw------- 1 root root 254, 4 2009-07-26 16:26 d0p4


```And no /dev/md0 exists anymore!

Also mdstat shows this
```

root@ubuntu-raid:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md_d0 : inactive sda1[0](S)
      4192832 blocks

unused devices: <none>

```Any suggestions on what I am doing wrong would be greatly appreciated.
Thanks.

---

### Post by miegiel on 2009-07-26
Are you sure mdadm loads during boot up? If you delete the *splash* parameter from the kernel line of your default boot you can see if it loads and possibly an error message (see */boot/grub/menu.lst*).

---

### Post by Drunken on 2009-07-26
I tried that, no errors from what I can see, there was no splash anyway I don't think.

Also, after the reboot if I type I get:
```
root@ubuntu-raid:~# mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdc5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdc2
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: no RAID superblock on /dev/sdb
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: no uptodate device for slot 0 of /dev/md/0
mdadm: added /dev/sdb1 to /dev/md/0 as 1
mdadm: /dev/md/0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sdb
mdadm: No arrays found in config file or automatically
```

Where is the superblock supposed to be, sda1 or sdb1?
Also notice "/dev/sda1: Device or resource busy" would that mean that I failed because of that, or because it's already mounted as /dev/md/0 but just not active?

---

### Post by jkcrowell on 2009-07-28
I had essentially the same problem, and so have others on the forum.  The problem is, mdadm needs to have the /etc/mdadm/mdadm.conf file set up correctly.  Some sources have said this file isn't required, but it certainly seems to be.  The way to set it up correctly is:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```See this very similar thread:

[http://ubuntuforums.org/showthread.php?t=1225334]("http://ubuntuforums.org/showthread.php?t=1225334&highlight=mdadm")

The thing which really burnt me, was that apparently other linux installations have this file located at /etc/mdadm.conf.  However, Ubuntu has it in /etc/mdadm/mdadm.conf.  So I'd had my file configured correctly, but in the wrong location.  It didn't work that way.  When I rebuilt my array and edited the correct mdadm.conf, everything was peachy.

---

### Post by Drunken on 2009-07-28
Hey, yeah that works adding that line to the end of the config.
Thanks!

---

### Post by guneza on 2010-05-13
Ah, fantastic! Worked for me too!

---

