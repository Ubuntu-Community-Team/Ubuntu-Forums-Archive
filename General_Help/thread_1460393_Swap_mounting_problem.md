---
title: "Swap mounting problem"
date: 2010-04-22
forum: General Help
---

### Post by dinozzo on 2010-04-22
Hello, Im hoping you experts on here can help me. After installing a minimal install of ubuntu and then xbmc I have been using the system unaware that the linux swap file is not mounting onstartup! After a power failure I booted the machine up and noticed an error message along the lines of:

swapon: /dev/sdb1: swap failed : invalid argument
mountall: swapon /dev/sdb1 [511] terminated with status 255
mountall: Problem activating swap: /dev/sdb1

After a little bit of research I did the fdisk -l command and got this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         498     4000153+  83  Linux
/dev/sda3             499      182401  1461135847+  fd  Linux RAID autodetect

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         498     4000153+  82  Linux swap / Solaris
/dev/sdb3             499      182401  1461135847+  fd  Linux RAID autodetect

Which seems right to me. As you can see I have a partition at the begining of each drive - one for / and one for swap with the software raid (the remainder of each drive) as /home (I know its a bad idea but I just wanted all my storage in one place)

The blkid command is what I think shows the problem:

/dev/sda1: UUID="88f6491f-5aea-44f3-9bc3-94bccb835a59" TYPE="ext4"
/dev/sda3: UUID="96dd0157-0a82-503f-77fa-a4a4dbe3a8d5" TYPE="linux_raid_member"
/dev/sdb1: UUID="3956994c-cf33-7ebf-583d-9d2ea22c0dc8" TYPE="linux_raid_member"
/dev/sdb3: UUID="96dd0157-0a82-503f-77fa-a4a4dbe3a8d5" TYPE="linux_raid_member"
/dev/md0: UUID="48532a81-57f2-45e1-aaaf-af7cc27ffd4e" TYPE="ext4"

It says /dev/sdb1 is TYPE="linux_raid_member" when it shouldnt be.
How do I change it so that its type is not raid and a normal swap file system?
Long post for probably a short answer :)

Thanks in advance!

---

### Post by dinozzo on 2010-04-23
All I need to do is change /dev/sdb1 to a swap file partition, its not a member of any raid. How do I change partition attributes? Theres no data on it so it could be deleted and re-created as swap but I have no idea how to do this.

---

### Post by john newbuntu on 2010-04-23
I shouldn't be second guessing but are you sure it is not a raid member? Can you please post the outputs of:
```
mdadm --detail /dev/md0
cat /proc/mdstat
sudo blkid -c /dev/null
```

---

### Post by dinozzo on 2010-04-23
root@ubuntu:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Mar  4 08:44:10 2010
     Raid Level : raid0
     Array Size : 2922271488 (2786.90 GiB 2992.41 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar  4 08:44:10 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 96dd0157:0a82503f:77faa4a4:dbe3a8d5
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
-------------------------------------------------------------------

root@ubuntu:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdb1[1](S)
      4000064 blocks

md0 : active raid0 sdb3[1] sda3[0]
      2922271488 blocks 64k chunks

unused devices: <none>
-------------------------------------------------------------------

root@ubuntu:~# sudo blkid -c /dev/null
/dev/sda1: UUID="88f6491f-5aea-44f3-9bc3-94bccb835a59" TYPE="ext4"
/dev/sda3: UUID="96dd0157-0a82-503f-77fa-a4a4dbe3a8d5" TYPE="linux_raid_member"
/dev/sdb1: UUID="3956994c-cf33-7ebf-583d-9d2ea22c0dc8" TYPE="linux_raid_member"
/dev/sdb3: UUID="96dd0157-0a82-503f-77fa-a4a4dbe3a8d5" TYPE="linux_raid_member"
/dev/md0: UUID="48532a81-57f2-45e1-aaaf-af7cc27ffd4e" TYPE="ext4"

---

### Post by klemes on 2010-04-23
Edit

---

### Post by john newbuntu on 2010-04-23
/proc/mdstat indicates that sdb1 it is still a part of a raid array md1.  You need to somehow remove /dev/mdb1.  I must confess I am not a raid expert.  Perhaps some one else can pitch in here or if you are brave enough to experiment with the mdadm commands such as:
mdadm --manage /dev/md1 --remove /dev/sdb1
you can try it out.  But PLEASE get a second opinion on this.
[U]
AFTER[/U] you break or remove the array, this is how you would set up swap on /dev/sdb1(assuming it is set up as a swap partition.):
Run
```
sudo /sbin/mkswap /dev/sdb1
```This will give a UUID if successful.  Make a note of this.
Also backup /etc/fstab.
```
gksudo gedit /etc/fstab
```You should have only one swap line.  Edit the swap line as follows:
```
UUID=120d9c-12f9-4a8d-af87-68df7 none  swap  sw 0  0
```where the string after UUID= is the one you got above.  And finally:
```
sudo swapon -a
```Check swap on next reboot using "swapon -s"

---

