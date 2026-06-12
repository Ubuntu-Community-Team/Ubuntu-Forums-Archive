---
title: "can't mount ntfs partition located on other hard-drive"
date: 2010-12-19
forum: General Help
---

### Post by davidvandoren on 2010-12-19
Hi 
Does someone know how to reconfigure this?

I have three hard drives. 

1. Sata 1TB. It has Windows xp and ubuntu 10.10 on it 
2. old 30G drive. It has ubuntu 10.04 on it 
3. Old 120G with ubuntu 10.04

I installed the oses on each drive by disconnecting the others. So each drive has a boot record, and I can choose by pressing F11 at boot.

All ubuntus can see and mount the NTFS partition except the one I installed last.
It's on the 120G drive.

Can someone help me please?
thanks!



Here are the outputs from
[B]
sudo fdisk -l[/B]

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe64fe64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60878   489002503+   7  HPFS/NTFS
/dev/sda2           60879      121602   487759290+   f  W95 Ext'd (LBA)
/dev/sda5           60879       62817    15567433    b  W95 FAT32
/dev/sda6           62817       65248    19530752   83  Linux
/dev/sda7           65248      119957   439451648   83  Linux
/dev/sda8          119958      121602    13206528   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b23f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112412672   83  Linux
/dev/sdb2           13995       14594     4805633    5  Extended
/dev/sdb5           13995       14594     4805632   82  Linux swap / Solaris

Disk /dev/sdc: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a756

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3578    28733440   83  Linux
/dev/sdc2            3578        3738     1282049    5  Extended
/dev/sdc5            3578        3738     1282048   82  Linux swap / Solaris
  

**sudo blkid**
/dev/sda1: UUID="10B43725B4370D2A" TYPE="ntfs" 
/dev/sda5: UUID="8C0C-34AA" TYPE="vfat" 
/dev/sda6: UUID="b2b7d355-1e36-4344-8252-d93a551d4b52" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="2cdd50f2-ef67-449b-bc9c-cadd365a8053" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="5c131f24-e062-4591-8386-6904549ec82c" TYPE="swap" 
/dev/sdb1: UUID="348ef569-00a5-41b7-8f81-9f711902a5ee" TYPE="ext4" 
/dev/sdb5: UUID="1e4ced6a-f8af-425f-be35-a002719a9781" TYPE="swap" 
/dev/sdc1: UUID="15ed5434-5b04-4627-8e3d-c0a9d20afbef" TYPE="ext4" 
/dev/sdc5: UUID="07cc3d6f-8da8-4ede-844e-db092b259d2d" TYPE="swap" 

**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e4ced6a-f8af-425f-be35-a002719a9781 none            swap    sw              0       0


**cat /etc/mtab**
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/david/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=david 0 0

---

### Post by lmarmisa on 2010-12-19
Where is located the current operating system?. Is it located on /dev/sdb1?.

---

### Post by lmarmisa on 2010-12-19
The file **/etc/mtab** seems incorrect. Do not match the file **/etc/fstab**. mtab says /etc/sdb1 and fstab /dev/sda1. Which system are you running?.

---

### Post by davidvandoren on 2010-12-19
Thanks for the reply

I am on the 120g drive running ubuntu 10.04
right now.

---

### Post by davidvandoren on 2010-12-19
I am on the sdb1 right now.
Should I reedit the etc/fstab accordingly?

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> Thanks for the reply

I am on the 120g drive running ubuntu 10.04
right now.

According to file /etc/mtab the device /dev/sdb1 is your root partition. So, you are running your operating system stored in partition /dev/sdb1.

But, according to your first post, the contents of file /etc/fstab seems wrong because the device for / is /dev/sda1. This can be explained because you disabled the other hard drives during the installation.

I re***mend to substitute devices by UUIDs in your different files /etc/fstab.

You are unable to mount the drive /dev/sdab1 because this partition is already mounted. This is your root partition.

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> I am on the sdb1 right now.
Should I reedit the etc/fstab accordingly?

Please, type this ***mand:

```

mount

```

and post its output.

---

### Post by davidvandoren on 2010-12-19
> **lmarmisa said:**
> 

I re***mend to substitute devices by UUIDs in your different files /etc/fstab.

This is your root partition.

Thanks for the help 

But how do I do that? I have never done this before and it's over my head a bit.

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> Thanks for the help 

But how do I do that? I have never done this before and it's over my head a bit.

I will help you for these changes.

At the moment, post the output of the ***mand mount, please.

---

### Post by davidvandoren on 2010-12-19
**mount**
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdc1 on /media/15ed5434-5b04-4627-8e3d-c0a9d20afbef type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7 on /media/2cdd50f2-ef67-449b-bc9c-cadd365a8053 type ext3 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> **mount**
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdc1 on /media/15ed5434-5b04-4627-8e3d-c0a9d20afbef type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7 on /media/2cdd50f2-ef67-449b-bc9c-cadd365a8053 type ext3 (rw,nosuid,nodev,uhelper=udisks)

You have to edit the file /etc/fstab

```

sudo gedit /etc/fstab

```

Locate the line
```

/dev/sda1       /               ext4    errors=remount-ro 0       1

```

Change the line to

```

UUID=348ef569-00a5-41b7-8f81-9f711902a5ee       /               ext4    errors=remount-ro 0       1

```

Then save and exit.

Type this ***mand

```

cat /etc/fstab

```

and post its output.

---

### Post by davidvandoren on 2010-12-19
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=348ef569-00a5-41b7-8f81-9f711902a5ee       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e4ced6a-f8af-425f-be35-a002719a9781 none            swap    sw              0       0

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=348ef569-00a5-41b7-8f81-9f711902a5ee       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e4ced6a-f8af-425f-be35-a002719a9781 none            swap    sw              0       0

I believe the file /etc/fstab is fixed now.

Type this ***mand now and post its output:

```

cat /etc/default/grub

```

---

### Post by davidvandoren on 2010-12-19
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=348ef569-00a5-41b7-8f81-9f711902a5ee       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e4ced6a-f8af-425f-be35-a002719a9781 none            swap    sw              0       0
david@david-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Un***ment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the ***mand `vbeinfo'
#GRUB_GFXMODE=640x480

# Un***ment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Un***ment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Un***ment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=348ef569-00a5-41b7-8f81-9f711902a5ee       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e4ced6a-f8af-425f-be35-a002719a9781 none            swap    sw              0       0
david@david-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Un***ment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the ***mand `vbeinfo'
#GRUB_GFXMODE=640x480

# Un***ment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Un***ment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Un***ment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Thanks. Type these two ***mands now:
```

sudo grub-install /dev/sdb
sudo update-grub

```

Of course, post the output.

A question, please. Do you see on the forums 3 strange asterisks replacing the string C-O-M?

---

### Post by davidvandoren on 2010-12-19
> **lmarmisa said:**
> 

A question, please. Do you see on the forums 3 strange asterisks replacing the string C-O-M?

Yes I do and was wondering myself about this!


**sudo update-grub**
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-26-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 10.10 (10.10) on /dev/sda7
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sdc1
done

Thanks I thing this looks right doesn't it?

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> Yes I do and was wondering myself about this!


**sudo update-grub**
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-26-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 10.10 (10.10) on /dev/sda7
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sdc1
done

Thanks I thing this looks right doesn't it?

Do you remember if the output of the ***mand "**sudo grub-install /dev/sdb**" was 

```

Installation finished. No error reported.

```

or something like that?.

---

### Post by davidvandoren on 2010-12-19
[B]


sudo grub-install /dev/sdb[/B]

Installation finished. No error reported.



Still had the window open

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> [B]


sudo grub-install /dev/sdb[/B]

Installation finished. No error reported.



Still had the window open

I believe that your Ubuntu 10.04 installed on /dev/sdb1 is fixed.

You should check the other two Ubuntu systems on /dev/sda7 and /dev/sdc1. You could try to post the contents of their files /etc/fstab and /etc/mtab.

---

### Post by davidvandoren on 2010-12-19
/dev/sdc1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=15ed5434-5b04-4627-8e3d-c0a9d20afbef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=07cc3d6f-8da8-4ede-844e-db092b259d2d none            swap    sw              0       0


/dev/sda7 / ext3 rw,errors=remount-ro,***mit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext3    errors=remount-ro 0       1
/dev/sda6       /boot           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=5c131f24-e062-4591-8386-6904549ec82c none            swap    sw              0       0

---

### Post by lmarmisa on 2010-12-19
> **davidvandoren said:**
> /dev/sdc1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=15ed5434-5b04-4627-8e3d-c0a9d20afbef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=07cc3d6f-8da8-4ede-844e-db092b259d2d none            swap    sw              0       0


/dev/sda7 / ext3 rw,errors=remount-ro,***mit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext3    errors=remount-ro 0       1
/dev/sda6       /boot           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=5c131f24-e062-4591-8386-6904549ec82c none            swap    sw              0       0

I see inconsistencies here too.

Please post the files of one of the two systems. But, very important, identify its partition.

---

### Post by lmarmisa on 2010-12-19
> **lmarmisa said:**
> I see inconsistencies here too.

Please post the files of one of the two systems. But, very important, identify its partition.

Hmmm.

Sorry. I was wrong.

The info seems correct.

We could modify the file /etc/fstab of the hard drive /dev/sda for the inclussion of UUIDs. But the info seems correct.

---

### Post by davidvandoren on 2010-12-19
Thanks every ubuntu install can now mout all partitions.

Thanks a lot.
And I will mark this thread as solved.

---

