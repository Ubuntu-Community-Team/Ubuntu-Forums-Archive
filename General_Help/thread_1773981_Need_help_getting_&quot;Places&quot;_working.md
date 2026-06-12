---
title: "Need help getting &quot;Places&quot; working"
date: 2011-06-02
forum: General Help
---

### Post by wetzeldc on 2011-06-02
On my new system "Places" does not show any of the partitions.  On /dev/sda I was expecting to see "/", "/home", "/opt", and the NTFS partition with a mounting point /Windows and a label of "Win".  This is the drive I am going to run on.  /dev/sdb is going to be used to backup /dev/sda. 
My old computer was a dual boot system, Ubuntu and XP, that was setup by GRUB.  I had access to the NTFS partition from both systems.  Shutting down and booting got to be a pain.  On the new computer the plan is to run XP on VMware Player and have access to the NTFS partition from both Ubuntu and XP.
So given the following information, what changes do I need to make AND how do I make them?

david@No2:~$ sudofdisk -l
sudofdisk: command not found
david@No2:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25496   204796588+   7  HPFS/NTFS
/dev/sda2   *       25497       31870    51199155   83  Linux
/dev/sda3           31871       56729   199679887    5  Extended
/dev/sda5           31871       50992   153597433+  83  Linux
/dev/sda6           50993       55454    35840983+  83  Linux
/dev/sda7           55455       56729    10241406   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00058219

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       26261   210941451    7  HPFS/NTFS
/dev/sdb2           26262       32909    53400060   83  Linux
/dev/sdb3           32910       57956   201190027+  83  Linux
david@No2:~$ 

david@No2:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdb2 on /tmp type ext4 (rw,commit=0)
/dev/sda5 on /home type ext4 (rw,commit=0)
/dev/sdb3 on /usr type ext4 (rw,commit=0)
/dev/sda6 on /opt type ext4 (rw,commit=0)
/dev/sdb1 on /dos type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
david@No2:~$ 

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=65e59f94-f2a2-433c-9607-b7112eb96737 /               ext4    errors=remount-ro 0       1
# /dos was on /dev/sdb1 during installation
UUID=3DFD19DD391613A2 /dos            ntfs    defaults,umask=007,gid=46 0       0
# /home was on /dev/sda5 during installation
UUID=b64c5dc1-6285-4fe6-9a89-3a66de1dfad3 /home           ext4    defaults        0       2
# /opt was on /dev/sda6 during installation
UUID=4fe19a9f-665c-4b2f-90cf-a95eebef8339 /opt            ext4    defaults        0       2
# /tmp was on /dev/sdb2 during installation
UUID=7fc2aa6f-82cc-4aae-977d-76df40470d06 /tmp            ext4    defaults        0       2
# /usr was on /dev/sdb3 during installation
UUID=fe9e5c9d-6c33-445e-8cab-5b68bb704512 /usr            ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=511CC91B123010FB /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=7409b942-3d22-4060-8c6c-e4fda3d352fa none            swap    sw              0       0

david@No2:~$ sudo blkid -c /dev/nul
[sudo] password for david: 
/dev/sda1: LABEL="Win" UUID="511CC91B123010FB" TYPE="ntfs" 
/dev/sda2: UUID="65e59f94-f2a2-433c-9607-b7112eb96737" TYPE="ext4" 
/dev/sda5: UUID="b64c5dc1-6285-4fe6-9a89-3a66de1dfad3" TYPE="ext4" 
/dev/sda6: UUID="4fe19a9f-665c-4b2f-90cf-a95eebef8339" TYPE="ext4" 
/dev/sda7: LABEL="Swap" UUID="7409b942-3d22-4060-8c6c-e4fda3d352fa" TYPE="swap" 
/dev/sdb1: LABEL="WinB" UUID="3DFD19DD391613A2" TYPE="ntfs" 
/dev/sdb2: UUID="7fc2aa6f-82cc-4aae-977d-76df40470d06" TYPE="ext4" 
/dev/sdb3: UUID="fe9e5c9d-6c33-445e-8cab-5b68bb704512" TYPE="ext4" 
david@No2:~$

---

### Post by TeoBigusGeekus on 2011-06-03
****Nevermind****

---

### Post by mcduck on 2011-06-03
Everything seems to work like it should, the Places-menu isn't even supposed to show partitions mounted elsewhere than inside /media. The / partition will show as your filesystem, /home partition will show as /home and so on, they are just parts of the same directory tree regardless of if they are located on different drives or partitions.

You can add bookmarks to the locations if you want, that will add them into Places and the sidebar in file manager. Just go to the location you wish to add as bookmark and hit Ctrl+D, or select Bookmarks->Add Bookmark from the file manager's menu.

---

