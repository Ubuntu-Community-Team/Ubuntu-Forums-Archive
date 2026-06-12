---
title: "no cd/dvd rom"
date: 2011-11-20
forum: General Help
---

### Post by xdweaver on 2011-11-20
I upgraded from 10.04 to 11.10. I can not use my cd/dvd rom. I tried to auto mount it and failed. here is my fstab info. please help me get this working. 


wendy@wendy-HP-Pavilion-dv5-Notebook-PC:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=238dc64c-1253-4d87-8e67-ad5ab77bcf62 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=12498404-308e-459b-b9d3-99dba9597c04 none            swap    sw              0       0

---

