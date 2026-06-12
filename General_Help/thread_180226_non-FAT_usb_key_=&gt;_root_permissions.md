---
title: "non-FAT usb key =&gt; root permissions"
date: 2006-05-21
forum: General Help
---

### Post by 5hundy on 2006-05-21
I have searched through the forums for a while and it seems like some people have similar problems but so far I have not seen any real conclusion to this issue:

I have a usb key using a FAT filesystem and everything works great. **If I change the fs to ext2, reiser, etc. it will auto-mount but the user will not have write permissions.** This is the case on both dapper and breezy. I assume this is a bug since I see no reason why this should only work right on FAT filesystems.

Running mount gives me: 
/dev/sda1 on /media/usbdisk type ext2 (rw,noexec,nosuid,nodev)

I tried this:
created a /media/usbdisk dir as root. Added:
/dev/sda1        /media/usbdisk  auto    rw,user  0       0
Of course the "user" here just makes it so the user can mount the device - this has nothing to do with access permissions

I assume the issue here is that some script somewhere is doing the wrong thing. I'd run strace and figure it out but since the auto-mount feature is not started on the command line I don't know how.

---

### Post by aysiu on 2006-05-21
Next time you have it mounted, paste this into the terminal: ```
sudo chmod -R 777 /media/usbdisk
```

---

### Post by 5hundy on 2006-05-21
Fantastic. Thanks! :D

---

