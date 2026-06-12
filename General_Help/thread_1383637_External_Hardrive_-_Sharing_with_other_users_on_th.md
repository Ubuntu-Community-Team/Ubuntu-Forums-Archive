---
title: "External Hardrive - Sharing with other users on the same computer"
date: 2010-01-17
forum: General Help
---

### Post by eric_1982 on 2010-01-17
I am having issues with sharing an external hard drive with other users on a computer. For example if I reboot and login with user A and then logout and login with user B, I am not able to mount the external hard drive. If I reboot and login with user B first, I can then access the external hard drive with user B but not user A. Is there a way that both users can use the drive without having to reboot every time? 

I am assuming this is some sort of security issue. If I login with the second user and go to /mnt/external harddrive I get a permission error."You do not have the permissions necessary to view the contents of "External Drive"." If I login with the first user and try to set the permission it doesn't give me the ability?

Any help would be greatly appreciated. Thanks!

---

### Post by Leppie on 2010-01-17
i think you might have forgotten to unmount the drive before logging off.

---

### Post by eric_1982 on 2010-01-17
I completly over look that. That seems to fix the issue. Is there a way that I can have a script run at logout to unmount that device?

---

### Post by Leppie on 2010-01-17
you could add a line to your etc/gdm/PostSession/Default, something like this:
```
umount /mnt/External\ Drive
```
this should execute the command at every log off

---

### Post by eric_1982 on 2010-01-17
Thank you so much! I made the change in that file and it worked perfectly. Thanks again!

---

### Post by johnnynb on 2010-01-17
Why not just mount it and as root change the permissions on 
the mount point to allow all uses to access the drive

mount /mnt/disk /dev/sdxx etc
   su to root
chmod 777 /mnt/disk

---

### Post by Leppie on 2010-01-17
> **eric_1982 said:**
> Thank you so much! I made the change in that file and it worked perfectly. Thanks again!
glad it's working as you want it to :)

---

