---
title: "Hard drive ownership"
date: 2011-05-08
forum: General Help
---

### Post by wildmanne39 on 2011-05-08
Hi everyone, I installed a second hard drive but I can not access it, I get a permissions denied, I have 2 ubuntu books but all I can find is how to change ownership for a file not a hard drive, can anyone tell me the exact command and way that I need to go about changing the ownership of the drive? Thanks to everyone in advance, I really appreciate the help.

---

### Post by lmarmisa on 2011-05-08
Type this command and post the result:

```

sudo fdisk -l

```

---

### Post by wildmanne39 on 2011-05-08
> **lmarmisa said:**
> Type this command and post the result:

```

sudo fdisk -l

```
Hi, this what it showed.
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00045a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36472   292961308+   7  HPFS/NTFS
/dev/sda2           36473       36497      194560   83  Linux
/dev/sda3           36497       77826   331969368+   5  Extended
/dev/sda5   *       36498       36522      200812+  83  Linux
/dev/sda6           36523       77571   329718784   83  Linux
/dev/sda7           77571       77826     2046976   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536   83  Linux
larry@larry-pc:~$ 

```
Thank you for your help.

---

### Post by lmarmisa on 2011-05-08
You have defined one Linux partition in the new hard drive. Please, type these commands and post here the results:

```

sudo parted -l
sudo blkid
mount

```

---

### Post by wildmanne39 on 2011-05-08
> **lmarmisa said:**
> You have defined one Linux partition in the new hard drive. Please, type these commands and post here the results:

```

sudo parted -l
sudo blkid
mount

```
Hi, this is the out come.
```
sudo parted -l
[sudo] password for larry: 
Model: ATA SAMSUNG HD642JJ (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  300GB  300GB   primary   ntfs
 2      300GB   300GB  199MB   primary   ntfs
 3      300GB   640GB  340GB   extended
 5      300GB   300GB  206MB   logical                   boot
 6      300GB   638GB  338GB   logical   ext4
 7      638GB   640GB  2096MB  logical   linux-swap(v1)


Model: ATA ST3500620AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4


larry@larry-pc:~$ sudo blkid
/dev/sda1: LABEL="Windows 7" UUID="53F77D961726314D" TYPE="ntfs" 
/dev/sda2: LABEL="windows7" UUID="208A99724BA83135" TYPE="ntfs" 
/dev/sda6: UUID="3eaea03d-a852-4807-b541-32aa2a3627ab" TYPE="ext4" 
/dev/sda7: UUID="a93687ff-b299-44a8-b4ac-b7d0871c7523" TYPE="swap" 
/dev/sdb1: UUID="3246650c-0794-47e0-89f9-3dcfaf7ffb21" TYPE="ext4" 
larry@larry-pc:~$ mount

/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/larry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=larry)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sdb1 on /media/3246650c-0794-47e0-89f9-3dcfaf7ffb21 type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

Thank you.

---

### Post by lmarmisa on 2011-05-08
The ext4 partition of the hard drive /dev/sdb is mounted.

If you wish to create a folder owned by your user in that partition, type these commands:

```

sudo mkdir /media/3246650c-0794-47e0-89f9-3dcfaf7ffb21/MyData
sudo chown -R larry:larry /media/3246650c-0794-47e0-89f9-3dcfaf7ffb21/MyData

```

You should be able to create your files or folders in the new directory.

Have you added a line to the file /etc/fstab for mounting automatically your hard drive?.

---

### Post by wildmanne39 on 2011-05-08
> **lmarmisa said:**
> The ext4 partition of the hard drive /dev/sdb is mounted.

If you wish to create a folder owned by your user in that partition, type these commands:

```

sudo mkdir /media/3246650c-0794-47e0-89f9-3dcfaf7ffb21/MyData
sudo chown -R larry:larry /media/3246650c-0794-47e0-89f9-3dcfaf7ffb21/MyData

```

You should be able to create your files or folders in the new directory.

Have you added a line to the file /etc/fstab for mounting automatically your hard drive?.

Hi,no did not, I used gparted I thought it would do it automatically. Thank so much, and if you give the exact command I will do that.
I actually am trying to change my virtual hard drives for virtualbox to that drive.

---

### Post by lmarmisa on 2011-05-08
> **wildmanne39 said:**
> Hi,no did not, I used gparted I thought it would do it automatically. Thank so much, and if you give the exact command I will do that.

A previous question. You have a dual boot system with Windows 7 and Ubuntu. If you define an ext4 partition on your second hard drive, you will be unable to access this partition from Windows 7. Do you like this solution?. Or perhaps would you prefer to share the second hard drive for both systems?.

---

### Post by wildmanne39 on 2011-05-08
> **lmarmisa said:**
> A previous question. You have a dual boot system with Windows 7 and Ubuntu. If you define an ext4 partition on your second hard drive, you will be unable to access this partition from Windows 7. Do you like this solution?. Or perhaps would you prefer to share the second hard drive for both systems?.

I do not need to access the second drive from windows 7 I almost never use window 7 just keep it for an emergency. But will it prevent me from booting into windows 7 when I restart the computer if  I need too?

---

### Post by lmarmisa on 2011-05-08
> **wildmanne39 said:**
> I do not need to access the second drive from windows 7 I almost never use window 7 just keep it for an emergency. But will it prevent me from booting into windows 7 when I restart the computer if  I need too?

No, no problem at all. You will be able to boot into Ubuntu or Windows 7. The only limitation will be the access from Windows 7 to the second drive. Anyway, you could use GParted in the future for shrinking your huge /dev/sdb1 ext4 partition and then define a second ntfs partition if you would like it. So, no problem if you define the partition as ext4 now and this is fine for performance.

I will send the instructions for automounting your second hard drive but I would appreciate if you could give me a label for this partition.

---

### Post by wildmanne39 on 2011-05-08
> **lmarmisa said:**
> No, no problem at all. You will be able to boot into Ubuntu or Windows 7. The only limitation will be the access from Windows 7 to the second drive. Anyway, you could use GParted in the future for shrinking your huge /dev/sdb1 ext4 partition and then define a second ntfs partition if you would like it. So, no problem if you define the partition as ext4 now and this is fine for performance.

I will send the instructions for automounting your second hard drive but I would appreciate if you could give me a label for this partition.
vbox is good for me, it it is allowed. Thank you very much.

---

### Post by lmarmisa on 2011-05-08
> **wildmanne39 said:**
> vbox is good for me, it it is allowed. Thank you very much.

Thanks.

You have to create a directory for mounting the drive. Type this command:

```

sudo mkdir /media/vbox

```

Now you have to edit the file **/etc/fstab**:

```

sudo gedit /etc/fstab

```
Add these two lines at the bottom of file:
```

# vbox on /dev/sdb1
UUID=3246650c-0794-47e0-89f9-3dcfaf7ffb21 /media/vbox ext4 rw,nosuid,nodev,uhelper=hal 0 1

```

Then, save and exit.

Reboot your system and verify that the partition **vbox** has been automatically mounted.

```

mount

```

---

### Post by wildmanne39 on 2011-05-08
> **lmarmisa said:**
> Thanks.

You have to create a directory for mounting the drive. Type this command:

```

sudo mkdir /media/vbox

```

Now you have to edit the file **/etc/fstab**:

```

sudo gedit /etc/fstab

```
Add these two lines at the bottom of file:
```

# vbox on /dev/sdb1
UUID=3246650c-0794-47e0-89f9-3dcfaf7ffb21 /media/vbox ext4 rw,nosuid,nodev,uhelper=hal 0 1

```

Then, save and exit.

Reboot your system and verify that the partition **vbox** has been automatically mounted.

```

mount

```

Hi, thank you very much that fixed my problem. About 2 months ago I installed gentoo in virtualbox for the challenge and it was just that, but the hand book is pretty darn good, so it made it doable. Even though I have been using ubuntu for a long time it can still be hard sometimes to find the exact info needed, but I love this forum everyone is usually very helpful, I am looking for a way to help too, I just have not find it yet. Thanks again,your help is very appreciated.:D

---

### Post by lmarmisa on 2011-05-08
> **wildmanne39 said:**
> Hi, thank you very much that fixed my problem. About 2 months ago I installed gentoo in virtualbox for the challenge and it was just that, but the hand book is pretty darn good, so it made it doable. Even though I have been using ubuntu for a long time it can still be hard sometimes to find the exact info needed, but I love this forum everyone is usually very helpful, I am looking for a way to help too, I just have not find it yet. Thanks again,your help is very appreciated.:D

It has been a pleasure to help you. Do not hesitate to send me a private message if you find some problems when you change your virtual disks.

Best regards,

Luis

---

