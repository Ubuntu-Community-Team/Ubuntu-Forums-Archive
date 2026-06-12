---
title: "Can't acces second hard drive"
date: 2012-05-20
forum: General Help
---

### Post by navbor on 2012-05-20
Hello All,
 
I have Ubuntu Server 10.10 installed and I have 7 client PC's all on Windows 7. 
 
I am new to this, so please be nice. 
 
I have managed to set-up and configure the server correctly I think. I have 3 HDD's in the server (1 System, 2 Public-Data, 3 Private-Data). All the hardware is working on the server and I am able to access the server from the first client PC.
 
I have already installed Samba and created a share to both the data drives. I can happily access sdb1, but the same is not true for sbc1. As far as I can see the settings for both drives are identical. Creating files on sdb1 is also no problem.
 
I have both drives partitioned as linux partitions (83) and both of them have been formatted using "sudo mkfs.ext3 /dev/sd*1.
 
The seetings in the smb.conf file for both shares are identical. The mount in fstab for both drives are also identical. The owners and permissions for both drives are also identical. 
 
Here are my configuration files:
 
fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=3bc3d86d-ed96-44c3-8722-56ad1ab3748f / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=e0d97230-00be-4ae6-a953-92cd2a0cc549 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /mnt/sdb1 ext3 defaults 0 0
/dev/sdc1 /mnt/sdc1 ext3 defaults 0 0

```

smb.conf
```

[global]
 
## Browsing/Identification 
###
# Change this to the workgroup/NT-domain name your Samba server will part of
 
workgroup = VIZMEC-WINDOWS
encrypt passwords = yes
wins support = yes
 
 
[V-M_PUBLIC]
comment = All VIZ-MEC public files
path = /mnt/sdb1
valid users = Rob
public = no
writable = yes
 
[V-M_PRIVATE]
comment = All VIZ-MEC private files
path = /mnt/sbc1
valid users = Rob
public = no
writable = yes

```
There are many more lines in smb.conf, but those are the only ones i fiddled with.


I am able to access the server via puTTY, so network is good, 
 
This is the error I get when I try to access the private share from the windows machine
 
> Windows cannot access [\\Vizmec\v-m_private]("file://vizmec/v-m_private")
 
Check the spelling of the name. Otherwise, there might be a problem with your network......
 
I am not sure what other information to make available to help fault find this issue, but any advice would be most welcome.
 
Thanks
 
Here is the out put from some commands:
 
```
administrator@vizmec:/etc$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb1 on /mnt/sdb1 type ext3 (rw)
/dev/sdc1 on /mnt/sdc1 type ext3 (rw)
 
 
administrator@vizmec:/etc$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 440G 1.1G 417G 1% /
none 4.0G 292K 4.0G 1% /dev
none 4.0G 0 4.0G 0% /dev/shm
none 4.0G 600K 4.0G 1% /var/run
none 4.0G 0 4.0G 0% /var/lock
/dev/sdb1 459G 199M 435G 1% /mnt/sdb1
/dev/sdc1 459G 199M 435G 1% /mnt/sdc1
 
administrator@vizmec:/etc$ sudo fdisk -l
[sudo] password for administrator:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004faea

Device Boot Start End Blocks Id Sy stem
/dev/sda1 * 1 58336 468581376 83 Li nux
/dev/sda2 58336 60802 19802113 5 Ex tended
/dev/sda5 58336 60802 19802112 82 Li nux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58584d91

Device Boot Start End Blocks Id Sy stem
/dev/sdb1 1 60801 488384001 83 Li nux


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed29272c

Device Boot Start End Blocks Id Sy stem
/dev/sdc1 1 60801 488384001 83 Li nux
 
administrator@vizmec:/etc$ ls -l /mnt
total 8
drwxrwxrwx 4 nobody nogroup 4096 2012-05-16 20:13 sdb1
drwxrwxrwx 3 nobody nogroup 4096 2012-05-16 17:30 sdc1

```

---

### Post by 2F4U on 2012-05-20
Shouldn't that

path = /mnt/**sbc1**

be instead configured as

path = /mnt/**sdc1**

---

### Post by navbor on 2012-05-20
Hello 2F4U
 
Thanks very much for pointing that out. That works perfectly now. I was so busy looking for a deeply technical error, that I overlooked the obvious.

---

### Post by 2F4U on 2012-05-20
You are welcome. In my experience, many problems are caused by simple things. Don't worry.

---

### Post by navbor on 2012-05-20
Indeed!
 
Is there anyway to mark this as solved?

---

