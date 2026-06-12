---
title: "Boot from drive image"
date: 2011-08-05
forum: General Help
---

### Post by gizmo720 on 2011-08-05
I am trying to boot from an ext4 file I have on my windows partition. To do this I am attempting to modify the initrd.img file. The file itself is located in C:/filesystems/root.ext4 in my windows partition (sda3) 

In the begining of the mountroot() function I added
```
mkdir /windows
mount.ntfs /dev/sda3 /windows
```

I am booting with the following commands in grub 1.98:
```
        
linux   /boot/vmlinuz-2.6.32-33-generic root=/windows/filesystems/root.ext4
initrd  /initrd.loop

```

This drops me to the shell within initrd.img. The folder /windows exists but is empty. When I type```
mount.ntfs /dev/sda3 /windows
exit
```

the computer boots into the file like I want it to. I think the problem is that the correct modules for ntfs partions have not been loaded at the time I call mount in the script. If this is the case where should I put my code, otherwise is there any other way of doing this.

---

