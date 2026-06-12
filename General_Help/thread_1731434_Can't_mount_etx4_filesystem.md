---
title: "Can't mount etx4 filesystem"
date: 2011-04-17
forum: General Help
---

### Post by Slyke on 2011-04-17
For some reason I get the following error when trying to mount a partition in my hard drive:

> Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sda7,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Some more help from dmesg | tail:
> [ 1261.867432] FAT: bogus number of reserved sectors
[ 1261.867437] VFS: Can't find a valid FAT filesystem on dev sda7.
[ 1300.391980] FAT: bogus number of reserved sectors
[ 1300.391984] VFS: Can't find a valid FAT filesystem on dev sda7.
[ 1392.565743] FAT: bogus number of reserved sectors
[ 1392.565748] VFS: Can't find a valid FAT filesystem on dev sda7.
[ 1503.338978] EXT4-fs (sda7): VFS: Can't find ext4 filesystem
[ 1523.089089] EXT4-fs (sda7): VFS: Can't find ext4 filesystem
[ 1782.293612] FAT: bogus number of reserved sectors
[ 1782.293616] VFS: Can't find a valid FAT filesystem on dev sda7.


If I format (Disk Utility) the drive to FAT, it works correctly. If I format it to NTFS, ext3 or ext4 it comes up with that error when trying to mount.

I'll be storing files on this drive that are larger then 4GBs, otherwise I'd be happy with just FAT.

I can format and mount correctly with:
> sudo mkfs -t ext4 /dev/sda7

But if I try:
> sudo mkfs.ext4 -n 'extraSpace' /dev/sda7

I get:
> mke2fs 1.41.12 (17-May-2010)
mkfs.ext4: invalid blocks count - /dev/sda7

I wish to be able to name the drive.

Any suggestions?

---

### Post by kiyop on 2011-04-17
How about executing the following?
```
sudo mke2fs -t ext4 -L extraSpace /dev/sda7
```Please refer to:
```
man mke2fs
```

By the way, you can use Gparted. You can install Gparted with Synaptic or 
```
sudo apt-get update
sudo apt-get install gparted
```

"System"->... ->"Gparted"

---

### Post by Morbius1 on 2011-04-17
I'm getting lost. Please post the output of the following commands:
```
cat /etc/fstab
sudo blkid -c /dev/null
```

---

### Post by Slyke on 2011-04-17
> **kiyop said:**
> How about executing the following?
```
sudo mke2fs -t ext4 -L extraSpace /dev/sda7
```Please refer to:
```
man mke2fs
```

By the way, you can use Gparted. You can install Gparted with Synaptic or 
```
sudo apt-get update
sudo apt-get install gparted
```

"System"->... ->"Gparted"

Yup, I also had tried with gParted, but didn't think it worth mentioning, as it had the same results as Disk Utility.

I'll do those commands and let you know how it goes!


> **Morbius1 said:**
> I'm getting lost. Please post the output of the following commands:
```
cat /etc/fstab
sudo blkid -c /dev/null
```

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc              proc  nodev,noexec,nosuid  0  0  
/dev/sda1                                  /                  ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=6453901d-f57f-4584-9b25-ff6118f8dc7f  none               swap  sw                   0  0  
/dev/sda5                                  /media/mainServer  ext4  users                0  0  
/dev/sda7                                  /media/extraSpace    vfat  users,user           0  0  


> sudo blkid -c /dev/null
[sudo] password for slyke: 
/dev/sda1: UUID="35955014-062a-4fe3-89ef-fb57a58da7a0" TYPE="ext4" 
/dev/sda5: LABEL="mainServer" UUID="8e49db5b-f6e4-4b90-9c7a-4fb5eccbc322" TYPE="ext4" 
/dev/sda6: UUID="6453901d-f57f-4584-9b25-ff6118f8dc7f" TYPE="swap" 
/dev/sda7: UUID="36c10a34-36fd-4809-aafd-116b6e2c08eb" TYPE="ext4" 




Here's the results:
> sudo mke2fs -t ext4 -L extraSpace /dev/sda7
mke2fs 1.41.12 (17-May-2010)
Filesystem label=extraSpace 
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
16613376 inodes, 66432000 blocks
3321600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
2028 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 36 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


Same thing when I try to mount it (I'm just using Places menu).

---

### Post by Morbius1 on 2011-04-17
Change this:
>  /dev/sda7                                  /media/extraSpace    vfat  users,user           0  0                        To this:
```
/dev/sda7 /media/extraSpace ext4 defaults,noatime 0 2
```Run the following command to test for errors ( and post them is there are any ) and mount the partition:
```
sudo mount -a
```I am assuming you already created /media/extraSpace at some point. If not:
```
sudo mkdir /media/extraSpace
```

[COLOR=Blue]Note:[/COLOR] You will have to do a chmod and / or a chown after the partition is mounted if you want to access the partition as someone other than root.

---

### Post by kiyop on 2011-04-17
You must remove wrong configuration about /dev/sda7 (vfat) in /etc/fstab

Thanks Morbius1

---

### Post by Slyke on 2011-04-17
Thanks!

That fixed it.

I don't know how it got set as that in the first place though.

> sudo gedit /etc/fstab

---

