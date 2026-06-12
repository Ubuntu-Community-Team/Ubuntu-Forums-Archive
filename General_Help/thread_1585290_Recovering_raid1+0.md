---
title: "Recovering raid1+0"
date: 2010-09-30
forum: General Help
---

### Post by harlan@bloomenterprises.o on 2010-09-30
Hello Everyone,
  I tried to upgrade my Ubuntu 9.10 to 10.04.  This didn't go very well at all.  I ended up having to re-install from scratch using 10.04 Desktop (64-bit).  Annoying, but that is not my main problem.  I was able to copy all my files from the boot drive.

  Now I'm trying to get my Raid 1+0 running again.  The rebuilt system seems to find the md0 and md1 Raid 1 partitions just fine.

  Here is the output from /proc/mdstat:


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d3 : inactive md1[1](S)
      312568512 blocks
       
md1 : active raid1 sdd1[0] sde1[1]
      312568576 blocks [2/2] [UU]
      # ls -l /dev/md*
brw-rw---- 1 root disk   9,   0 2010-09-30 08:41 /dev/md0
brw-rw---- 1 root disk   9,   1 2010-09-30 08:41 /dev/md1
brw-rw---- 1 root disk   9,   3 2010-09-30 09:26 /dev/md3
brw-rw---- 1 root disk 254, 192 2010-09-30 08:41 /dev/md_d3
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p1 -> md/d3p1
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p2 -> md/d3p2
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p3 -> md/d3p3
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p4 -> md/d3p4

/dev/md:
total 0
brw------- 1 root root 254, 192 2010-09-30 08:41 d3
brw------- 1 root root 254, 193 2010-09-30 08:41 d3p1
brw------- 1 root root 254, 194 2010-09-30 08:41 d3p2
brw------- 1 root root 254, 195 2010-09-30 08:41 d3p3
brw------- 1 root root 254, 196 2010-09-30 08:41 d3p4

md0 : active raid1 sdc1[1] sdb1[0]
      312568576 blocks [2/2] [UU]
      
unused devices: <none>


  Here is the /etc/mdadm/mdadm.conf:

# cat /etc/mdadm/mdadm.conf 
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b1bcd910:b39402bb:ef8990be:4392515d
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=0f16eddc:14f8aa64:ef8990be:4392515d

# This file was auto-generated on Thu, 30 Sep 2010 08:23:05 -0500
# by mkconf $Id$


  Here is the /dev/md* listing:


# ls -l /dev/md*
brw-rw---- 1 root disk   9,   0 2010-09-30 08:41 /dev/md0
brw-rw---- 1 root disk   9,   1 2010-09-30 08:41 /dev/md1
brw-rw---- 1 root disk   9,   3 2010-09-30 09:26 /dev/md3
brw-rw---- 1 root disk 254, 192 2010-09-30 08:41 /dev/md_d3
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p1 -> md/d3p1
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p2 -> md/d3p2
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p3 -> md/d3p3
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p4 -> md/d3p4

/dev/md:
total 0
brw------- 1 root root 254, 192 2010-09-30 08:41 d3
brw------- 1 root root 254, 193 2010-09-30 08:41 d3p1
brw------- 1 root root 254, 194 2010-09-30 08:41 d3p2
brw------- 1 root root 254, 195 2010-09-30 08:41 d3p3
brw------- 1 root root 254, 196 2010-09-30 08:41 d3p4


  When I try to assemble the md3:

# mdadm --assemble --auto=yes /dev/md3   /dev/md0 /dev/md1
mdadm: cannot open device /dev/md1: Device or resource busy
mdadm: /dev/md1 has no superblock - assembly aborted

  I tried adding an ARRAY entry to the mdadm.conf file:
ARRAY /dev/md3 level=raid0 num-devices=2 devices=/dev/md0,/dev/md1

  That didn't work either.

  Any ideas or suggestions?  The VM's contained on the Raid1+0 contain my VM's that need to get running ASAP!

Thanks,

Harlan...

---

### Post by psusi on 2010-09-30
It sounds like you already have mounted a partition on the first half of the mirror.  Check what sudo mount shows.

---

### Post by harlan@bloomenterprises.o on 2010-09-30
Here is the output from mount:

# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/harlan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harlan)
/dev/sdf1 on /media/b46e16d6-09cf-4a1b-acfe-7268f15d3a58 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg1 on /media/73dce735-0387-4403-9a3b-e0063b717fb9 type ext3 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by psusi on 2010-09-30
Wait, look at md_d3.  That looks like it already activated the stripe as md_d3 and found 4 partitions on it.

---

### Post by harlan@bloomenterprises.o on 2010-09-30
According to /proc/mdstat, md_d3 only has md1 as part of it, and it is inactive.

Here is what happens when I try to mount md_d3:


# mount /dev/md_d3 /data
mount: you must specify the filesystem type
root@filesrv:~# mount /dev/md_d3 /data -t ext2
mount: wrong fs type, bad option, bad superblock on /dev/md_d3,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@filesrv:~# mount /dev/md_d3 /data -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/md_d3,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@filesrv:~# mount /dev/md_d3 /data -t ext4
mount: wrong fs type, bad option, bad superblock on /dev/md_d3,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

  md_d3/md3 should be ext3 or 4.  I don't remember which one was used, but mount should detect it.

---

### Post by psusi on 2010-09-30
Try adding the md3 line back to the config file, then to get rid of the busy error when you try to activate it, you need to make md_d3 release it first.  Run sudo mdadm --stop /dev/md_d3.

---

### Post by harlan@bloomenterprises.o on 2010-09-30
I did the stop as you suggested:


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd1[0] sde1[1]
      312568576 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[1] sdb1[0]
      312568576 blocks [2/2] [UU]
      
unused devices: <none>
root@filesrv:~# ls -l /dev/md*
brw-rw---- 1 root disk   9,   0 2010-09-30 08:41 /dev/md0
brw-rw---- 1 root disk   9,   1 2010-09-30 08:41 /dev/md1
brw-rw---- 1 root disk 254, 192 2010-09-30 10:23 /dev/md_d3
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p1 -> md/d3p1
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p2 -> md/d3p2
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p3 -> md/d3p3
lrwxrwxrwx 1 root root        7 2010-09-30 08:41 /dev/md_d3p4 -> md/d3p4

/dev/md:
total 0
brw------- 1 root root 254, 192 2010-09-30 08:41 d3
brw------- 1 root root 254, 193 2010-09-30 08:41 d3p1
brw------- 1 root root 254, 194 2010-09-30 08:41 d3p2
brw------- 1 root root 254, 195 2010-09-30 08:41 d3p3
brw------- 1 root root 254, 196 2010-09-30 08:41 d3p4


I also added the line for the md3 into the mdadm.conf file - no change.  I did notice, however, lines showing up in the /var/log/daemon.log file:

Sep 30 10:23:44 filesrv mdadm[2724]: DeviceDisappeared event detected on md device /dev/md3

These seem to happen every time I stop/start the mdadm daemon.

---

### Post by harlan@bloomenterprises.o on 2010-09-30
I tried to assemble md3 again - it worked this time!!!!


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd1[0] sde1[1]
      312568576 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[1] sdb1[0]
      312568576 blocks [2/2] [UU]
      
unused devices: <none>
root@filesrv:~# mdadm --assemble --auto=yes /dev/md3   /dev/md0 /dev/md1
mdadm: /dev/md3 has been started with 2 drives.
root@filesrv:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid0 md0[0] md1[1]
      625137024 blocks 64k chunks
      
md1 : active raid1 sdd1[0] sde1[1]
      312568576 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[1] sdb1[0]
      312568576 blocks [2/2] [UU]
      
unused devices: <none>
root@filesrv:~# mount /dev/md3 /data


And I could mount it!  All my data is there as expected.  I'm not sure if it's going to survive a reboot, or if the md_d3 is going to show up again.  I've got some testing to do now.

psusi, Thank You very much for your help!!!

---

