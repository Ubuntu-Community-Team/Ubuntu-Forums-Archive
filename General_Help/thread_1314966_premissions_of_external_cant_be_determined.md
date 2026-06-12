---
title: "premissions of external cant be determined"
date: 2009-11-04
forum: General Help
---

### Post by burntresistor on 2009-11-04
permissions of external harddrive cant be determined
ever since I upgraded to 9.10 I've had this error which I think is why it hasnt let me attach mediatomb with the drive. How do I fix it do i need to reformat?

---

### Post by burntresistor on 2009-11-08
Its not just my external I checked my main hd and it also has been effected. I really need help](*,)  I try to right click the drive to change it that way it wont work. As soon as I click apply and close and open it back up again to see if it worked whatever I just did is gone. it says permissions of "/" cannot be determined and the other just says permissions of drivename cant be determined

---

### Post by oscurochu on 2009-11-08
Im just gonna take stab in the dark at this one. What type of filesystems are the partitions you are having problems with? Did you customize /etc/fstab previously?

---

### Post by burntresistor on 2009-11-08
> **oscurochu said:**
> Im just gonna take stab in the dark at this one. What type of filesystems are the partitions you are having problems with? Did you customize /etc/fstab previously?

no i didnt mess with fstab. 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=52f75355-70f2-4369-af11-7164269b0847 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cdb32725-24be-4be1-9aff-de888b7da9bd none            swap    sw              0       0


```
```

 sudo blkid
/dev/sda1: UUID="52f75355-70f2-4369-af11-7164269b0847" TYPE="ext4" 
/dev/sda5: UUID="cdb32725-24be-4be1-9aff-de888b7da9bd" TYPE="swap" 
/dev/sdb: LABEL="LaCie" UUID="0F40-095B" TYPE="vfat" 
/dev/sdc1: UUID="411C80AC517E1FE9" TYPE="ntfs" 
```



```

ls -l /media/
total 30
drwx------  1 burntresistor burntresistor 20480 2009-11-07 17:04 411C80AC517E1FE9
lrwxrwxrwx  1 root          root              6 2009-10-26 17:47 cdrom -> cdrom0
drwxr-xr-x  2 root          root           4096 2009-10-26 17:47 cdrom0
drwx------ 12 burntresistor burntresistor  4096 1969-12-31 16:00 LaCie
dr-x------  1 burntresistor burntresistor  2048 2007-09-28 10:47 TheWitcher

```

---

