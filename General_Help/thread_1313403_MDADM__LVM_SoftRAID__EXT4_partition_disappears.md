---
title: "MDADM / LVM SoftRAID / EXT4 partition disappears"
date: 2009-11-03
forum: General Help
---

### Post by arindrel on 2009-11-03
Hi, 
I'm a bit new to Linux, so apologies if I've posted too little/much info, or am totally barking up the wrong tree with what im trying to do.

I have built a PC to act as network file storage for some video editing I'm doing.  Boots ubuntu 9.10 of a regular 30gb ide hard disk.  (Athlon 6000+ duel core cpu, 2gb ram) 
Everything runs fine, no issues with Karmic whatsoever
I've then plugged 6x 1.5TB sata hard disks into the system (Onto the motherboard not a dedicated raid card).  Linux picks them up perfectly.  I was intending to use RAID level 10 on the drives to make a 4.5tb array.

I manage to set the array up fine and it works ok (providing you chmod a whole bunch of stuff).  However when i reboot the machine the array vanishes, along with any sign it ever existed.  Im pretty sure the data is there someplace (partitions don't just go missing after all).  Now i guess i was just expecting Logical volumes and volume groups to persist over a reboot, so all i can think of I've messed up some part of the setup.  Ill cut and paste the steps i went through below, hopefully someone can tell me what ive done wrong, and let me know how to get my raid array back

so the 6x 1.5tb drives im using to build the array are sda,sdb,sdc,sdd,sdf,sdg ... for some reason my 30gb ide hard disk is 'sde' but im not too bothered about that right now.  

```

rich@Orthanc:~$ sudo mdadm -v -C /dev/md2 -c 256 -n 6 -l 10 /dev/sd[abcdfg]1
mdadm: layout defaults to n1
mdadm: size set to 1465135872K
mdadm: array /dev/md2 started.
rich@Orthanc:~$ 


rich@Orthanc:~$ cat /proc/mdstat 
Personalities : [raid10] 
md2 : active raid10 sdg1[5] sdf1[4] sdd1[3] sdc1[2] sdb1[1] sda1[0]
      4395407616 blocks 256K chunks 2 near-copies [6/6] [UUUUUU]
      [>....................]  resync =  0.2% (12285760/4395407616) finish=366.2min speed=199461K/sec
      
unused devices: <none>
rich@Orthanc:~$ 

```

so mdadm seems to find em and build a softraid array of roughly the right size. So far so good.
so next i build the physical volume

```

rich@Orthanc:~$ sudo pvcreate /dev/md2
  Physical volume "/dev/md2" successfully created

rich@Orthanc:~$ sudo pvscan
  PV /dev/md2                      lvm2 [4.09 TB]
  Total: 1 [4.09 TB] / in use: 0 [0   ] / in no VG: 1 [4.09 TB]
rich@Orthanc:~$ 

rich@Orthanc:~$ sudo pvdisplay 
  --- Physical volume ---
  PV Name               /dev/md2
  VG Name               raid-vg
  PV Size               4.09 TB / not usable 2.25 MB
  Allocatable           yes 
  PE Size (KByte)       4096
  Total PE              1073097
  Free PE               1073097
  Allocated PE          0
  PV UUID               5MSPGT-lMOY-x5Ns-zI2c-ERPL-zS2o-gPhhXM
   
rich@Orthanc:~$ 

```

seems ok to me .. 4.09TB is effectively the full ((6*1.5)/2)tb from raid 10 given rounding errors etc
so next i create the volume group

```

rich@Orthanc:~$ sudo vgcreate raid-vg /dev/md2 
  Volume group "raid-vg" successfully created

rich@Orthanc:~$ sudo vgscan 
  Reading all physical volumes.  This may take a while...
  Found volume group "raid-vg" using metadata type lvm2
rich@Orthanc:~$ 

rich@Orthanc:~$ sudo vgdisplay 
  --- Volume group ---
  VG Name               raid-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               4.09 TB
  PE Size               4.00 MB
  Total PE              1073097
  Alloc PE / Size       0 / 0   
  Free  PE / Size       1073097 / 4.09 TB
  VG UUID               NFWIUg-NtBD-cy6G-G6g2-gpyL-NzA0-fb5f0Y
   
rich@Orthanc:~$ 

```

Then set the volume group to be active

```

rich@Orthanc:~$ sudo vgchange -a y raid-vg
  0 logical volume(s) in volume group "raid-vg" now active
rich@Orthanc:~$ 

```

then the logical volume goes on top of that

```

rich@Orthanc:~$ sudo lvcreate -L 4.09T -n raid-lv raid-vg
  Rounding up size to full physical extent 4.09 TB
  Logical volume "raid-lv" created
rich@Orthanc:~$ 


rich@Orthanc:~$ sudo lvscan
  ACTIVE            '/dev/raid-vg/raid-lv' [4.09 TB] inherit
rich@Orthanc:~$ 

rich@Orthanc:~$ sudo lvdisplay 
  --- Logical volume ---
  LV Name                /dev/raid-vg/raid-lv
  VG Name                raid-vg
  LV UUID                U0sX3i-uOm9-zT5t-4MNh-dzu8-PF0R-72hlLq
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                4.09 TB
  Current LE             1072169
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
rich@Orthanc:~$ 

```

and lastly , we format the lv with the ext4 filesystem and mount it up

```

rich@Orthanc:~$ sudo mkfs.ext4 -L raid-fs /dev/raid-vg/raid-lv
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=raid-fs
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
274481152 inodes, 1097901056 blocks
54895052 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
33506 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
rich@Orthanc:~$ 


rich@Orthanc:~$ sudo mount -L raid-fs -t ext4 /media/filestore
[sudo] password for rich: 
rich@Orthanc:~$ 

```

After all this the drive works perfectly (its owner is root so i had to chmod a subfolder to drop some test files in there, but that to be expected from all those sudos)

Now i switch the PC off, and come back an hour later.  Boots up fine, no error messages, nothing strange happens, but i cannot mount up the softraid file system ... i include my frantic keyboard mashings below
```

rich@Orthanc:~$ sudo mount -L raid-fs -t ext4 /media/filestore
mount: no such partition found
rich@Orthanc:~$ 
rich@Orthanc:~$ sudo pvscan
  No matching physical volumes found
rich@Orthanc:~$ sudo pvdisplay 
rich@Orthanc:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
rich@Orthanc:~$ sudo vgdisplay 
rich@Orthanc:~$ sudo lvscan 
rich@Orthanc:~$ sudo lvdisplay 
rich@Orthanc:~$ 
rich@Orthanc:~$ 
rich@Orthanc:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d2 : inactive sdg1[5](S)
      1465135936 blocks
       
unused devices: <none>


```
so this does not look good at all ... i can understand the fs needing manual re-mounting (as i didn't modify /etc/fstab yet) but the volume group and physical volumes being missing worries me.  

the block device /dev/raid-vg/raid-lv is missing (explaining why i couldn't mount it) and i cant find anything in /dev/mapper

i have these in /dev/
rich@Orthanc:/dev$ ls | grep 'md'
md
md_d2
md_d2p1
md_d2p2
md_d2p3
md_d2p4
rich@Orthanc:/dev$ 
but now i'm not really 100% sure what im looking at 

This is my 2nd time through the process above and the same thing has happened both times (the array is fine till a reboot).  Im pretty sure the steps above are correct, i just think im missing some tiny piece of information on how to re-activate the array on reboot

any assistance will be greatly appreciated

---

### Post by arindrel on 2009-11-06
solved
was a typo in my /etc/mdadm/mdadm.conf
it should have read
```
DEVICE /dev/sd[abcdfg]1
ARRAY /dev/md2 devices=/dev/sd[abcdfg]1

```

man mdadm.conf for the win

Forum admins - feel free to delete this thread as it was entirely my own error

---

