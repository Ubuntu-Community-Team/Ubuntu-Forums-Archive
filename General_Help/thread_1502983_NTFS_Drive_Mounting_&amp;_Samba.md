---
title: "NTFS Drive Mounting &amp; Samba"
date: 2010-06-06
forum: General Help
---

### Post by itiswhatitis on 2010-06-06
I have a 500GB secondary internal drive that I used to store all of my Windows files before I switched to Ubuntu.   In either operating system, I could access the files, but in Ubuntu I was always asked for my password before I could access it.

Since I used Samba to share the drive with the other Windows computers in my house, I had to make sure I always opened the drive once, then restart smbd.

After 10.04 was released, I wiped out my primary and put only Ubuntu on it.  I still had the same issue, but found a handy howto on adding the NTFS drive to my fstab, which eliminated my need to enter the password.  However, I still need to restart smbd before the drive is visible to other computers.  I think Samba is starting before the drive is mounted, but I'm not sure...

This is my fstab
```

#Second Drive, currently NTFS
 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6bca26a5-db88-45be-85b8-a420945adef9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=069d5371-45fb-45e1-9372-97b2a5d41174 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Second Drive, currently NTFS
UUID=9068070A6806EEB2 /media/ntfs ntfs-3g quiet,defaults,rw 0 0


```Can someone help me out with getting things in the right order so that everything comes up and I don't have to keep remembering to do this?

Thanks,

IIWII

---

