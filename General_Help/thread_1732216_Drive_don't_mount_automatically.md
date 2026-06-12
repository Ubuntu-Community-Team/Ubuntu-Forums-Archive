---
title: "Drive don't mount automatically"
date: 2011-04-17
forum: General Help
---

### Post by Ronobir on 2011-04-17
When I click on a drive to open then it says,(suppose for my drive named VIDEO)

[B]Unable to mount VIDEO
[/B]Error mounting: mount exited with exit code 1:helper failed with:
mount:only root can mount /dev/sda5 on media/sda5

But when I then manually mount using the command
sudo mount /dev/sda5 media/sda5

then it becomes ok.

How can I solve this problem?

---

### Post by thecamelcoder on 2011-04-18
The majority of information relate to drive mappings is stored in /etc/fstab. 

In general fstab is used for internal devices, CD/DVD devices, and network shares (samba/nfs/sshfs). 

Removable devices such as flash drives *can* be added to fstab, but are typically mounted by gnome-volume-manager and it is not recommended to include these as you can experience delays during boot.

Can you include in your post the output from 'sudo fdisk -l` and /etc/fstab. 

Thanks

):P

---

### Post by Ronobir on 2011-04-18
Thanks for ur prompt answer.

Output of 'sudo fdisk -l'

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbe8bbe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6540    52532518+   7  HPFS/NTFS
/dev/sda2            6541       15618    72914237+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           15619       38914   187117569    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5           15619       21554    47672320    7  HPFS/NTFS
/dev/sda6           21554       30692    73400320    7  HPFS/NTFS
/dev/sda7           30692       36946    50236416   83  Linux
/dev/sda8           37219       38914    13613056    7  HPFS/NTFS

```output of /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid              0  0  
/dev/sda8                                  /            ext4  defaults                         0  1  
# swap was on /dev/sda9 during installation
UUID=b03a3091-6b8d-45c6-a10d-ac7e2cfbe42c  none         swap  sw                               0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,ro,umask=000,user  0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000          0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,umask=000          0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,umask=000          0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,umask=000          0  0  
/dev/sda7                                  /media/sda7  ntfs  nls=iso8859-1,umask=000          0  0  
```

---

