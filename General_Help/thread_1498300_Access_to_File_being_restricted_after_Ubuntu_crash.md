---
title: "Access to File being restricted after Ubuntu crashed"
date: 2010-05-31
forum: General Help
---

### Post by flylehe on 2010-05-31
My Ubuntu 8.10 crashed due to the overheating problem of the CPU when I am opening some directory and intend to do some file transfer under Nautilus. After reboot, under gnome, all the files cannot be removed, their properties cannot be  viewed and they can only be opened, although all are still fine under terminal. I was wondering why is that and how can I fix it?

Here is some info hopefully helful:
```

    $ cat /etc/mtab  
    /dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0  
    tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0  
    /proc /proc proc rw,noexec,nosuid,nodev 0 0  
    sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0  
    varrun /var/run tmpfs rw,nosuid,mode=0755 0 0  
    varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0  
    udev /dev tmpfs rw,mode=0755 0 0  
    tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0  
    devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0  
    fusectl /sys/fs/fuse/connections fusectl rw 0 0  
    lrm /lib/modules/2.6.27-15-generic/volatile tmpfs rw,mode=755 0 0  
    /dev/sda8 /home ext3 rw,relatime 0 0  
    /dev/sda2 /windows-c vfat rw,utf8,umask=007,gid=46 0 0  
    /dev/sda5 /windows-d fuseblk rw,allow_other,blksize=4096 0 0  
    securityfs /sys/kernel/security securityfs rw 0 0  
    binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0  
    gvfs-fuse-daemon /home/tim/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tim 0 0  

```
    
Thanks and regards!

---

### Post by mikewhatever on 2010-05-31
Many files in Ubuntu are indeed read only, that's nothing new. Regardless, you may want to run the file system check to correct possible errors.

---

### Post by dv3500ea on 2010-05-31
For all the files you want to be able to read or write, run
```
sudo chmod ugo+rw files
```

---

### Post by mikewhatever on 2010-05-31
> **dv3500ea said:**
> For all the files you want to be able to read or write, run
```
sudo chmod ugo+rw files
```

This is a horrible advice!

---

### Post by flylehe on 2010-05-31
Thanks!

I am talking about the files that should not be read only but now become read-only under nautilus. Even looking at their properties is not possible  under nautilus. But under terminal all file operations are fine.

I was also wondering how to run the file system check to correct possible errors (even this might not help in my case)?

> **mikewhatever said:**
> Many files in Ubuntu are indeed read only, that's nothing new. Regardless, you may want to run the file system check to correct possible errors.

---

### Post by mikewhatever on 2010-05-31
```
sudo shutdown -F -r now
```

The command will reboot the computer, and an fsck check will be initiated on startup.

Edit: The command didn't do anything other then reboot for me, not sure why.

---

