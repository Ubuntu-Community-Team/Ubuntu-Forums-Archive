---
title: "How do I mount USB drive to multiple locations?"
date: 2010-02-10
forum: General Help
---

### Post by Eugene_Bondarenko on 2010-02-10
Hi, 

I have two storage drives that I will be sharing by FTP. One is internal 1TB ext4 HDD and another one is an external USB 1TB NTFS HDD. Both drives get mounted to /media and I am trying to set an additional mount point for each. For internal HDD everything works perfectly. I simply went to /etc/fstab and copied the line related to it. Now I have:
```

/dev/sdb5                                  /home/eugene/.MOUNT/sdb5  ext4         defaults               0  0  
/dev/sdb5                                  /media/sdb5               ext4         defaults               0  0  

```
which does exactly what I need.

I tried doing the same for the USB drive which produces unexpected results. The lines are
```

/dev/sdc1                                  /home/eugene/.MOUNT/sdc1  ntfs         defaults               0  0  
/dev/sdc1                                  /media/sdc1               ntfs         defaults               0  0  

```
This has the following results:
- in /media/Y (Y is label of this HDD) I have this HDD and can access all its contents which is good
- in /home/eugene/.MOUNT/sdc1 I don't have anything and this is bad
- in /media/sdc1 I have only one folder from this HDD and this folder is empty (on the HDD this folder is not empty) and this is somehow weird.

Could you please assist me with this and help sort things out?

---

### Post by gwpritch on 2010-02-10
Instead of trying to mount the usb drive to multiple locations, simply mount to the single point /media/sdc1 as you have and create simlinks from your other directories.
eg.

```
ln -s /media/sdc1 /home/eugene/.MOUNT/sdc1  
```

---

### Post by Eugene_Bondarenko on 2010-02-10
Yeah, I tried to do this however the FTP server I am using wants to have everything under one single directory. It doesn't allow symlinks to external locations (to locations outside the "home" directory of the FTP user).

Also I don't want to completely change the mount point because I have lots of stuff (mainly backup tools) configured to look for that external HDD at the existing location. That's why I am trying to create 2 mount points - this will keep both FTP and backup tools happy.

---

### Post by flippo on 2010-02-10
can you mount the directory where your FTP server wants it then make a symlink for your backups?

---

### Post by Eugene_Bondarenko on 2010-02-11
Yeah, that's actually a good idea! Thanks, I will try to solve the issue this way tonight and will let you know whether this works or not.

---

