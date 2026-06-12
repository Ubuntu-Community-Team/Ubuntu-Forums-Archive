---
title: "Restoreing default drive mount settings."
date: 2011-07-02
forum: General Help
---

### Post by anshulfy on 2011-07-02
Hi,

A week before I installed the PYSDM utility for automatic mount of windows partition during startup. Always it used to give warning saying that partition can not be mount. Now, I want to restore the previous setting. I uninstalled PYSDM but still it give the same annoying warning. Please help with restoring the default drive mount setting. 

Thanks in advance.
--
Anshul

---

### Post by dino99 on 2011-07-02
edit /etc/fstab, it should only have /home & swap, everything else is useless as we use mountall to deal "on demand" with needed devices/partition(s)

---

### Post by Morbius1 on 2011-07-02
The only way anyone is actually going to be able to help you is if they know how you are set up. Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by anshulfy on 2011-07-03
Hi Morbius,

Thanks for your reply. Following is the output of the commands you suggested me.

> anshul@anshulfy:~$ sudo blkid -c /dev/null
[sudo] password for anshul: 
/dev/sda1: LABEL="Anshul1" UUID="DAD83F1FD83EF979" TYPE="ntfs" 
/dev/sda5: LABEL="Anshul2" UUID="F20494F80494C151" TYPE="ntfs" 
/dev/sda6: UUID="46362796-4c75-480e-8cd2-e770a56807f5" TYPE="ext4" 
/dev/sda7: UUID="d8b51bf3-97e8-4986-8b31-471ee8294524" TYPE="ext4" 
/dev/sda8: UUID="2d259e1a-26fe-4620-8870-1307c1cebc8d" TYPE="ext4" 
/dev/sda9: UUID="76542670-d69f-4821-8473-867121fda0dc" TYPE="swap" 

anshul@anshulfy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda6 during installation
UUID=46362796-4c75-480e-8cd2-e770a56807f5  /               ext4  errors=remount-ro    0  1  
# /boot was on /dev/sda8 during installation
UUID=2d259e1a-26fe-4620-8870-1307c1cebc8d  /boot           ext4  defaults             0  2  
# /home was on /dev/sda7 during installation
UUID=d8b51bf3-97e8-4986-8b31-471ee8294524  /home           ext4  defaults             0  2  
# swap was on /dev/sda9 during installation
UUID=76542670-d69f-4821-8473-867121fda0dc  none            swap  sw                   0  0  
/dev/sdb4                                  /media/Anshul1  ntfs  defaults             0  0  
/dev/sdb1                                  /media/sdb1     ntfs  defaults             0  0  
/dev/sdb2                                  /media/sdb2     ntfs  defaults             0  0  
/dev/sdb3                                  /media/sdb3     ntfs  defaults             0  0  
/dev/sda5                                  /media/Anshul2  ntfs  defaults             0  0  


anshul@anshulfy:~$ mount
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
/dev/sda5 on /media/Anshul2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /home type ext4 (rw,commit=0)
/dev/sda8 on /boot type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/anshul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=anshul)
/dev/sda1 on /media/Anshul1_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)



---

### Post by Morbius1 on 2011-07-03
Your fstab references sdb partitions but blkid sees no sdb partitions so I would comment those lines out by placing a # sign in front of the line so that they look like this:
```
#/dev/sdb4  /media/Anshul1  ntfs  defaults             0  0  
#/dev/sdb1  /media/sdb1     ntfs  defaults             0  0  
#/dev/sdb2  /media/sdb2     ntfs  defaults             0  0  
#/dev/sdb3  /media/sdb3     ntfs  defaults             0  0  
```Not sure what you want to do with /dev/sda1 but if you want it to automount then I would add the following lin to fstab:
```
 /dev/sda1   /media/Anshul1  ntfs  defaults             0  0  
```Then I would do the following two steps:
[1] Unmount sda1:
```
sudo umount /media/Anshul1_
```[2] Run the following command that will test for errors and mount the new partitions:
```
sudo mount -a
```If it comes back with an error post them. If it comes back to the prompt then it ran successfully and you should see your your sda1 and sda5 partitions mounted.

---

### Post by anshulfy on 2011-07-03
Thank you very much Morbius, It worked.

---

