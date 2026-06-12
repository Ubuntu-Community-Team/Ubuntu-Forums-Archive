---
title: "can't mount xfs filesystem"
date: 2012-01-01
forum: General Help
---

### Post by Meph1st0 on 2012-01-01
I have a 1TB hard drive with three partitions.  one is a 2 GB swap partition, another is a 20GB ext3 root partition, and the last is an XFS partition with the remaining space on the hard drive used for it.

I just did a clean install of 11.10 and during the install I specified to have it format and install to the 20GB root partition and specified to do nothing with the XFS files system since I didn't want it to erase or format anything on that partition.

Now that the OS  is installed I want to mount the xfs partition but it's not working.  I type in the following:

```
sudo mount /dev/sda6 /media/mount
```
and I get an error saying:

```
mount: Cannot allocate memory
```

Searching with Google only brings up articles talking about being unable to mount windows file shares and getting the same error message.

Clearly this is nothing at all related to what I'm trying to do.

Any suggestions would be greatly appreciated.

---

### Post by Buntumatic on 2012-01-01
Try running ```
tail -f /var/log/messages
``` in another terminal when issuing mount command. Are you sure that filesystem is not automatically mounted already? Output of ```
mount
``` command will tell.

---

### Post by Meph1st0 on 2012-01-01
> **Buntumatic said:**
> Try running ```
tail -f /var/log/messages
``` in another terminal when issuing mount command. Are you sure that filesystem is not automatically mounted already? Output of ```
mount
``` command will tell.

I read someone doing that earlier and tried it...but found shortly afterward that I don't have a /var/log/messages file.

It simply doesn't exist.

should I create one?

here is the output of the mount command:

```
jbrown@browndvr:~$ cd /var/log
jbrown@browndvr:/var/log$ ls
alternatives.log  dmesg           lastlog    pm-powersave.log
apache2           dmesg.0         lightdm    pycentral.log
apt               dmesg.1.gz      mail.err   samba
auth.log          dpkg.log        mail.log   syslog
boot              faillog         mysql      udev
boot.log          fontconfig.log  mysql.err  ufw.log
bootstrap.log     fsck            mysql.log  unattended-upgrades
btmp              installer       mythtv     wtmp
ConsoleKit        jockey.log      news       Xorg.0.log
dist-upgrade      kern.log        ntpstats   Xorg.0.log.old
jbrown@browndvr:/var/log$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
jbrown@browndvr:/var/log$
```

---

### Post by Meph1st0 on 2012-01-01
Additional details:

I booted into the livecd and then installed gparted.  In gparted I selected the partition and selected the Check option to check the file system.

It errored out with the same error message when it attempted to temporarily mount the file system in order for it to run its checks.  Here's the output of that log file:
```

GParted 0.7.0 --enable-libparted-dmraid

Libparted 2.3
Check and repair file system (xfs) on /dev/sda6  00:00:09    ( ERROR )
     	
calibrate /dev/sda6  00:00:00    ( SUCCESS )
     	
path: /dev/sda6
start: 42973938
end: 1953520064
size: 1910546127 (911.02 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:00:09    ( SUCCESS )
     	
xfs_repair -v /dev/sda6
     	
Phase 1 - find and verify superblock...
- block cache size set to 172296 entries
Phase 2 - using internal log
- zero log...
zero_log: head block 2 tail block 2
- scan filesystem freespace and inode maps...
- found root inode chunk
Phase 3 - for each AG...
- scan and clear agi unlinked lists...
- process known inodes and perform inode discovery...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- process newly discovered inodes...
Phase 4 - check for duplicate blocks...
- setting up duplicate extent list...
- check for inodes claiming duplicate blocks...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
Phase 5 - rebuild AG headers and trees...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- reset superblock...
Phase 6 - check inode connectivity...
- resetting contents of realtime bitmap and summary inodes
- traversing filesystem ...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- traversal finished ...
- moving disconnected inodes to lost+found ...
Phase 7 - verify and correct link counts...

XFS_REPAIR Summary Sun Jan 1 17:42:02 2012

Phase Start End Duration
Phase 1: 01/01 17:41:54 01/01 17:41:54
Phase 2: 01/01 17:41:54 01/01 17:41:57 3 seconds
Phase 3: 01/01 17:41:57 01/01 17:42:02 5 seconds
Phase 4: 01/01 17:42:02 01/01 17:42:02
Phase 5: 01/01 17:42:02 01/01 17:42:02
Phase 6: 01/01 17:42:02 01/01 17:42:02
Phase 7: 01/01 17:42:02 01/01 17:42:02

Total run time: 8 seconds
done
grow file system to fill the partition  00:00:00    ( ERROR )
     	
create temporary mount point (/tmp/gparted_tmp_xfs_mount_point)  00:00:00    ( SUCCESS )
mount /dev/sda6 on /tmp/gparted_tmp_xfs_mount_point  00:00:00    ( ERROR )
     	
mount -v -t xfs /dev/sda6 /tmp/gparted_tmp_xfs_mount_point
     	
mount: Cannot allocate memory
remove temporary mount point (/tmp/gparted_tmp_xfs_mount_point)  00:00:00    ( SUCCESS ) 
```

I also ran xfs_repair but did not receive any errors or indications of a corrupted file system.

The machine has 2 GB of RAM and a 2GB swap partition.  Not sure how much more memory it needs in order to mount it.

Also, according to Gparted the partition 911.02 GB in size, with 317.53 GB used and 593.49 GB free.

---

### Post by rsvancara on 2012-01-01
Which kernel are you running...

uname -r 

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by Meph1st0 on 2012-01-02
Okay, so I got this worked out.  It's still a strange issue in general but here's what I ended up doing.

I happened to have a bootable USB stick running Clonezilla.  I was using it to save images of the root partition in case I messed anything up with it.  So I booted off it and used the command line feature to mount and then unmount the partition.  I'm guessing that at some previous point it had been unmounted improperly.

Once I was able to get it mounted that way it's now mounting just fine in ubuntu.  Thanks for your help folks.

---

